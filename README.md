# Programming
项目简介：通过对共享单车数据集进行探索性分析，了解季节、天气、工作日、节假日、温度、风速等因素是如何影响共享单车使用率的，并用不同方法建模预测共享单车需求，以期找到拟合程度最好的预测模型。
运行环境：Python 3.9.12
运行包的版本：matplotlib 3.5.1；numpy 1.21.5；pandas 1.4.2；plotnine 0.10.1；prettytable 3.6.0；seaborn 0.11.2；scikit-learn1.0.2；statsmodels 0.13.2；
复现步骤：
class DataLoad():
    def __init__(self, csv_path):
        self.csv_path = csv_path
        self.data = pd.read_csv(self.csv_path)
        self.data.sample(frac=1.0, replace=True, random_state=1)
    def getHeader(self):
        return list(self.data.columns.values)
    def getData(self):
        #按照8：2的比例划分为训练集和测试集
        split_train = int(80/100 * len(self.data))
        train = self.data[:split_train]
        test = self.data[split_train:]
        return train, test
    def getFullData(self):
        return self.data
