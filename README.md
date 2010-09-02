MooTools TrackInstances Class Mutator
=====================================

Create an **instances** array property for a class, to contain all of its instances. The array can be used to alter all instances at once, for example -

* A widget class that its instances need to be repositioned upon a window resize
* Stop all music players at once
* Hide all instances of a popup class at once

How to use
----------

Just add **TrackInstances:true** to your class definition, **after** the initialize method.


	var MyClass=new Class({
		initialize:function () {
		},

		TrackInstances:true,

		recalcPosition:function () {
			// something that recalculates position or any other task that should happen on all instances
		}
	});

	var x=new MyClass();
	var y=new MyClass();

	MyClass.instances; // [x, y]
	MyClass.instances.length; // 2

	// from another code:
	window.addEvent("resize",function () {
		MyClass.instances.each(function (instance) {
			instance.recalcPosition();
		});
	});