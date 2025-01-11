k近邻的算法实现api

```
#实例化API
estimator = KNeighborsClassifier(n_neighbors=1)
#使用fit方法进行训练
estimator.fit(x, y)
estimator.predict([[1]])
```