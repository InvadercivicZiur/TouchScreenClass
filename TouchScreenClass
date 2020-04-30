extends TouchScreenButton
class_name TouchScreenClass

var on_area = false

func _ready():
	self.connect("pressed", self, "_on_self_pressed",[],0)
	self.connect("released", self, "_on_self_released",[],0)

func get_drag_direction(drag, drag_margin):
	var drag_direction = Vector2.ZERO
	
	if drag.x <= -drag_margin:
		if drag.y <= -drag_margin:
			drag_direction = Vector2(-1, -1) #up-left
	if drag.x >= drag_margin:
		if drag.y <= -drag_margin:
			drag_direction = Vector2(1, -1) #up-right
	if drag.x <= -drag_margin:
		if drag.y >= drag_margin:
			drag_direction = Vector2(-1, 1) #down-left
	if drag.x >= drag_margin:
		if drag.y >= drag_margin:
			drag_direction = Vector2(1, 1) #down-right
	
	if drag.x >= -drag_margin and drag.x <= drag_margin:
		if drag.y >= drag_margin:
			drag_direction = Vector2.DOWN
	if drag.x >= -drag_margin and drag.x <= drag_margin:
		if drag.y <= -drag_margin:
			drag_direction = Vector2.UP
	if drag.y >= -drag_margin and drag.y <= drag_margin:
		if drag.x >= drag_margin:
			drag_direction = Vector2.RIGHT
	if drag.y >= -drag_margin and drag.y <= drag_margin:
		if drag.x <= -drag_margin:
			drag_direction = Vector2.LEFT
	
	if on_area == true:
		return drag_direction

func _on_self_pressed():
	if get_parent().has_method(str("_on_",self.get_name(),"_pressed")) == true:
		get_parent().call(str("_on_", self.get_name(), "_pressed"))
	on_area = true

func _on_self_released():
	if get_parent().has_method(str("_on_", self.get_name(), "_released")) == true:
		get_parent().call(str("_on_", self.get_name(), "_released"))
	on_area = false
