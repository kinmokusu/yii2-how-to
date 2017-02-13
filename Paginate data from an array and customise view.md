<h1>Paginate data from an array and customise view</h1>
Consider the array  
$data = [
          'one' => 'data from first row',
          'two' => 'data from second row',
          'three' => 'data from third row',
          'four' => 'data from fourth row',
          'five' => 'data from fifth row',
          ];
<h3>Controller</h3>
    public function actionView($id)
    {
        $pages = new Pagination(['totalCount' => count($data), 'defaultPageSize'=>2]);
        $models = array_slice($data, $pages->offset, $pages->pageSize);
        return $this->render('view', [
            'pages' => $pages,
            'models' => $models,
        ]);
    }

 
 
<h3>View</h3>
          <?php foreach ($models as $key => $value) :?>
          <p><?=$value?></p>
          <?php endforeach?>
          <div class="pagination col-md-12 text-center">
              <?= LinkPager::widget(['pagination' => $pages,]);?> 
          </div>
