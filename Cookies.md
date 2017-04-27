<h1>Using Cookies</h1>
<p>
The part of the application dealing with request and response directly is controller. Therefore, cookies should be read and sent in controller. [<a href='http://www.yiiframework.com/doc-2.0/guide-runtime-sessions-cookies.html#cookies'>guide</a>]
</p>

<div>

    public function actionAdd()
    {
        $cookies = \Yii::$app->response->cookies;
        $cookies->add(new \yii\web\Cookie([
            'name' => 'test',
            'value' => 'here',
        ]));
    }
</div>

<div>

    public function actionRead()
    {
        $cookies = \Yii::$app->request->cookies;
        var_dump($cookies->get('test'));
    }
</div>

<div>

    public function actionRemove()
    {
        $cookies = \Yii::$app->response->cookies;
        $cookies->remove('test');
    }
    
</div>
