<h1>Paginate data from an array and customise view</h1>

<div>

    Consider the array  
    $data = [
              'one' => 'data from first row',
              'two' => 'data from second row',
              'three' => 'data from third row',
              'four' => 'data from fourth row',
              'five' => 'data from fifth row',
              ];
</div>
<h3>Controller</h3>

<div>

    <?php
    use yii\widgets\LinkPager;
    ?>
    <?php
    public function actionView($id)
    {
        $pages = new Pagination(['totalCount' => count($data), 'defaultPageSize'=>2]);
        $models = array_slice($data, $pages->offset, $pages->pageSize);
        return $this->render('view', [
            'pages' => $pages,
            'models' => $models,
        ]);
    } ?>
</div>
 
 
<h3>View</h3>
<div>

          <?php
          use yii\widgets\LinkPager;
          ?>
          <?php foreach ($models as $key => $value) :?>
            <p><?=$value?></p>
          <?php endforeach?>
          <div class="pagination col-md-12 text-center">
              <?= LinkPager::widget(['pagination' => $pages,]);?> 
          </div>
</div>
