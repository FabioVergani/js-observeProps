(function(global){'use strict';

	function each(m,cb){var e=m.slice(0),f=cb,i=0;while(e.length!==0){f(e.shift(),i++);}}

	function isdefined(o){return o!=='' && typeof(o)!=='undefined';}
	isdefined.array=function(oa){var o=oa;return isdefined(o) && Array.isArray(o);};


	function observe(obj,props){

	 function f(prop){
				var o=observed;
				var p = prop;
				var pnew = p + "new";
				var pold = p + "old";
				o[pold] = o[p];
				Object.defineProperty(o,p,{
				 get : function(){return this[pnew];},
				 set : function(x){
					var e=this;
					console.log("old-value: ", this[pold]);
					console.log("new-value: ", x);
					this[pnew] = x;
					this[pold] = this[pnew];
				 }
				});


	 }

	 var m=props,observed=obj;
	 each(isdefined.array(m)?m:Object.keys(observed),f);
	}

	//test:
	var person = {
	 name : "jack",
	 age : 26
	};

function logHeapSize(){console.log('usedJSHeapSize:',window.performance.memory.usedJSHeapSize);}
logHeapSize();
	observe(person);
logHeapSize();
	person.name = "john";
	person.age = 27;
logHeapSize();

})(window);
