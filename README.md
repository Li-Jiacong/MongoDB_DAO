# 对MongoDB进行DAO层的封装
## 使用注意点
**里面有一个`init(collction,obj)`函数,每次使用这个js文件前一定要进行传参**  
  
    
**这是一个实例，对名为`"users"`的`collection`的`username`创建索引(‘1’表示升序)**  

	//执行函数，对数据库的某个collection创建索引
	//每次调用函数时要记得对init()进行传参
	init("users",{ "username": 1});
	function init(collction,obj){
		//对数据库进行一个初始化
		_connectDB(function(err, db){
			if (err) {
				console.log(err);
				return;
			}
			db.collection(collction).createIndex(
				obj,
				null,
				function(err, results) {
					if (err) {
						console.log(err);
						return;
					}
					console.log("索引建立成功");
				}
			);
		});
	}


