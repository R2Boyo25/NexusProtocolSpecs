### Terms
- Nodes: The individual joints on a [[Avatar]].

### Ownership
Node paths are for the client's [[Avatar]]. Nodes cannot be accessed or updated by other clients.

### Attributes
- nodePath: `String`; /grandparent/parent/child; Path to the node
- position: `Vec3`; {xPos: int, yPos: int, zPos: int}; Stores the position of a node.
- lastPosition: `Vec3`; {xVel: int, yVel: int, zVel: int}; Stores the previous position of a node; Used for calculating velocity of held objects (and anything a client or server might need it for, such as collisions). 
- rotation: `Vec3`; {xRot: int, yRot: int, zRot: int}; Stores the rotation of a node.
- lastRotation: `Vec3`; {xRVel: int, yRVel: int, zRVel: int}; Stores the previous rotation of a node. Used for calculating rotationalVelocity of held objects.

### Updates
Nodes can be updated with a request like this:
```json
{
	"type":     "nodeUpdate",
	"nodePath": "/path/to/node",
	"rotation": {
		"x": 0,
		"y": 0,
		"z": 0
	},
	"position": {
		"x": 0,
		"y": 0,
		"z": 0
	}
}
```

### Retrieving Attributes
```json
{
	"type":   "retrieveNodeAttributes",
	"nodePath": "/path/to/node",
}
```
Returns a dictionary/map containing all Public attributes of the Node.