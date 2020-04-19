LGBM(lite GBM)   
===
- lite GBM  
    - GBM(Gradient Bossting Algorithm)  
    This algoritm uses for prediction of regression and classification.  
    It is based by boosting. The boosting algorithm makesfrom weak classifier to strong classifier.  
    The GBM works same thing of the boosting algorithm by gradient.  
    It is using decision tree.
    - lite GBM  
    This algorithm is fast. Because it's tree growth vertical.  
    So, it avoid overfitting.  
    It use less memory and has high accuracy. 
- how to ues  
    ```python
    import ligthgbm as lgb
    train_ds = lgb.Dataset(X_train, label=y_train)
    test_ds = lgb.Dataset(X_val, label=y_val)
    params = {
        'learning_rate': 0.01,
        'max_depth': 16,
        'boosting': 'gbdt',
        'objective': 'regression',
        'metric': 'mse',
        'is_training_metric': True,
        'num_leaves': 144,
        'feature_fraction': 0.9,
        'bagging_fraction': 0.7,
        'bagging_freq': 5,
        'seed':2020
    }

    model = lgb.train(params, train_ds, 1000, test_ds, verbose_eval=100, early_stopping_rounds=100)
    y_pred = model.predict(X_val)
    ```


