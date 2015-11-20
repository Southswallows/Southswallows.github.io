---
layout: post
category: 技术
title: Backbone
tags: web
---

![BackBones.js](http://7xkeeu.com1.z0.glb.clouddn.com/backbone.png)
##简单介绍

**Backbone.js是一套JavaScript框架与RESTful JSON的应用程序界面。也是一套大致上符合MVC架构的编程范型。Backbone.js以轻量为特色，只需依赖一套Javascript 函式库即可运行。常被用来开发单页的互联网应用程序，以及用来维护网络应用程序的各种部分（例如多使用者与服务器端）的同步。**
###[API中文文档](http://www.css88.com/doc/backbone/)

##Backbone中主要的学习介绍
- Model是根据现实数据建立的抽象，比如人（People）；
- Collection是Model的一个集合，比如一群人；
- View是对Model和Collection中数据的展示，把数据渲染（Render）到页面上；
- Router是对路由的处理，就像传统网站通过url现实不同的页面，在单页面应用（SPA）中通过Router来控制前面说的View的展示。

		var Todo = Backbone.Model.extend({
	  		initialize: function(){
	      console.log('This model has been initialized.');
	 	 }
		});
	
		// 我们可以创建一个不带参数的 Todo 实例
		
		var todo1 = new Todo();
		
		// log 会在浏览器的控制台 console 中打印
		
		console.log(JSON.stringify(todo1));
	
		// 创建时加上属性参数
		var todo2 = new Todo({
		  title: 'Check the attributes of both model instances in the console.',
		  completed: true
		});
	
		// log 输出: {"title":"Check the attributes of both model instances in the console.","completed":true}
		
		console.log(JSON.stringify(todo2));

- 有时候你希望你的模型有默认属性，就可以使用 defaults 方法。

		var Todo = Backbone.Model.extend({
  			defaults: {
    			title: '',
    			completed: false
  			}
		});

- 如果你想在模型被改变时收到通知，可以绑定监听器，一般都在 initialize() 中绑定监听器：

		var Todo = Backbone.Model.extend({
 		 defaults: {
  		  title: '',
   		 completed: false
 		 },
 		
		 initialize: function(){
    		console.log('This model has been initialized.');
   			 this.on('change', function(){
       		 console.log('- Values for this model have changed.');
  		  });
 		 }
		});

		
		var myTodo = new Todo();
		
		myTodo.set('title', 'The listener is triggered whenever an attribute value changes.');
		console.log('Title has changed: ' + myTodo.get('title'));
		
		
		myTodo.set('completed', true);
		console.log('Completed has changed: ' + myTodo.get('completed'));
		
		myTodo.set({
		  title: 'Changing more than one attribute at the same time only triggers the listener once.',
		  completed: true
		});

- 集合是模型的有序组合，我们可以在集合上绑定 "change" 事件，从而当集合中的模型发生变化时fetch（获得）通知，集合也可以监听 "add" 和 "remove" 事件， 从服务器更新，并能使用 Underscore.js 提供的方法。
- 集合中的模型触发的任何事件都可以在集合身上直接触发，所以我们可以监听集合中模型的变化： documents.on("change:selected", ...)
- 在下面的集合中，我们创建 TodoCollection ，它会包含 todo 模型:

		var Todo = Backbone.Model.extend({
		  defaults: {
		    title: '',
		    completed: false
		  }
		});
		
		var TodosCollection = Backbone.Collection.extend({
		  model: Todo
		});
		
		var myTodo = new Todo({title:'Read the whole book', id: 2});
		
		var todos = new TodosCollection([myTodo]);
		console.log("Collection size: " + todos.length); // Collection size: 1
- Collections.fetch() 方法通过向指定的 URL 发送 GET 请求来从服务器端获取模型数据，一旦接收到数据，就会自动调用 set() 更新集合。

		var Todo = Backbone.Model.extend({
		  defaults: {
		    title: '',
		    completed: false
		  }
		});
		
		var TodosCollection = Backbone.Collection.extend({
		  model: Todo,
		  url: '/todos'
		});
		
		var todos = new TodosCollection();
		todos.fetch(); // sends HTTP GET to /todos
- save() 方法会 POST 对应的 Model对象（json数据）到配置好的 url 上。

		var Todo = Backbone.Model.extend({
		  defaults: {
		    title: '',
		    completed: false
		  }
		});
		
		var TodosCollection = Backbone.Collection.extend({
		  model: Todo,
		  url: '/todos'
		});
		
		var todos = new TodosCollection();
		todos.fetch();
		
		var todo2 = todos.get(2);
		todo2.set('title', 'go fishing');
		todo2.save(); // sends HTTP PUT to /todos/2
		
		todos.create({title: 'Try out code samples'}); // sends HTTP POST to /todos and adds to collection
- 从Server端删除模型`todo2.destroy();`

		var Todo = Backbone.Model.extend({
		  defaults: {
		    title: '',
		    completed: false
		  }
		});
		
		var TodosCollection = Backbone.Collection.extend({
		  model: Todo,
		  url: '/todos'
		});
		
		var todos = new TodosCollection();
		todos.fetch();
		
		var todo2 = todos.get(2);
		todo2.destroy(); // sends HTTP DELETE to /todos/2 and removes from collection

- 创建一个新的视图，扩展 Backbone.View 创建视图：

		var TodoView = Backbone.View.extend({
		
		  tagName:  'li',
		
		  // 缓存单个项的模版函数
		  todoTpl: _.template( "An example template" ),
		
		  events: {
		    'dblclick label': 'edit',
		    'keypress .edit': 'updateOnEnter',
		    'blur .edit':   'close'
		  },
		
		  initialize: function (options) {
		    this.options = options || {};
		  },
		
		  // 重新渲染 todo 的 title
		  render: function() {
		    this.$el.html( this.todoTpl( this.model.attributes ) );
		    this.input = this.$('.edit');
		    return this;
		  },
		
		  edit: function() {
		  },
		
		  close: function() {
		  },
		
		  updateOnEnter: function( e ) {
		  }
		});
		
		var todoView = new TodoView();
		
		// log view 实例相对应的 Dom 元素
		console.log(todoView.el); // log输出 <li></li>
- 视图的关键属性是 el 。el 是 DOM 元素的一个引用，所有的视图都需要它。视图使用 el 组织元素的内容然后一次性插入到 DOM 中，这样就能减少浏览器重新绘制的次数
- 有两种方法可以将 DOM 与视图关联起来：在视图中创建新元素随后再加入到 DOM 中或者引用已存在的DOM元素。
- 如果你想创建新元素，可以设置以下任意属性： tagName， id 与 className。el 会引用到你创建的元素。当没有指定 tagName 内容的时候，其值默认为 div 。在上面的例子中，将 tagName 设置成 'li' 就能创建 li 元素了。
- 下面的例子中创建了带有 id 与 class 属性的 ul 元素：

		var TodosView = Backbone.View.extend({
		  tagName: 'ul', 
		  className: 'container',                               
		  id: 'todos'
		});
		
		var todosView = new TodosView();
		console.log(todosView.el); // log输出 <ul id="todos" class="container"></ul>

- 上述代码创建了 DOM 元素，但还没有将它加入到 DOM 中去。你也可以像设置 CSS 选择器一样设置 el 来引用页面中的 DOM：

		el: '#footer'    
- 可以在创建实例的时候就这么做：

		var todosView = new TodosView({el: $('#footer')});
- Backbone events hash可以允许我们添加事件监听到el——用户自定义的选择器，或者未指定选择器的时直接监听到el。事件以{"事件名称 选择器": "回调函数"}的格式表示，支持大量的DOM事件，包括click, submit, mouseover, dblclick 还有更多。

		// A sample view
		var TodoView = Backbone.View.extend({
		  tagName:  'li',
		
		  // with an events hash containing DOM events
		  // specific to an item:
		  events: {
		    'click .toggle': 'toggleCompleted',
		    'dblclick label': 'edit',
		    'click .destroy': 'clear',
		    'blur .edit': 'close'
		  },