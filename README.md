首先需要建立对应的表：其中自定义字段选择P+N的格式，当然还有更好的办法。
创建自定义字段管理表，控制字段查看填写是否必填等权限。
表创建完成之后：需要创建自定义字段项：
 $model=new EventSign();
 $EventSign_count=EventSign::find()->where(['event_id'=>$id])->count();
 $data=yii::$app->request->post();
 $datas=yii::$app->request->post('EventSign');
 $model->type=$data['type'];//自定义字段名称
 for ($i=1;$i<=（循环最大数取决于P+N）;$i++)
 {
     $conn=EventSign::find()->where(['Field'=>'p'.($EventSign_count+$i),'event_id'=>$id])->one();
     if (empty($conn))
     {
          $model->Field='p'.($modes+$i);
          break;
      }
  }
