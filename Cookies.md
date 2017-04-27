<h1>Using Cookies</h1>

<div>
`
    public function actionAdd()
    {
        $cookies = \Yii::$app->response->cookies;
        $cookies->add(new \yii\web\Cookie([
            'name' => 'test',
            'value' => 'here',
        ]));
    }
    public function actionRead()
    {
        $cookies = \Yii::$app->request->cookies;
        var_dump($cookies->get('test'));
    }
    public function actionRemove()
    {
        $cookies = \Yii::$app->response->cookies;
        $cookies->remove('test');
    }
`
</div>
