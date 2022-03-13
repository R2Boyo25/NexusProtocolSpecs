### Terms
- Object: A model that can be moved around and interacted with by [[Avatar|Avatars]].

### Attributes
- grabbed: `bool`; Stores whether an object is grabbed by an [[Avatar]]. 
- grabbedBy: `String`; Stores who is currently holding the object.
- heldBy: `String`; Stores a path to the node on the [[Avatar]] that the object is held by.
- position: Public; `Vec3`; {xPos: int, yPos: int, zPos: int}; Stores the position of an object
- velocity: Private; `Vec3`; {xVel: int, yVel: int, zVel: int}; Stores the velocity of an object
- rotation: Public; `Vec3`; {xRot: int, yRot: int, zRot: int}; Stores the rotation of an object
- rotationalVelocity: Private; `Vec3`; {xRVel: int, yRVel: int, zRVel: int}; Stores the rotational velocity of an object

### Physics
The server should use the velocity and rotationalVelocity to move/rotate the object every physics timestep.

### When Grabbed
When an object is grabbed by an [[Avatar]], the movements of the node it is held by are copied to its position and rotation, velocity and rotationalVelocity is ignored when grabbed.

### Grabbing
```json
{
	"type":     "grabObject",
	"object":   "objectID",
	"nodePath": "/path/to/node"
}
```

### Dropping
```json
{
	"type":   "dropObject",
	"object": "objectID",
	"nodePath": "/path/to/node"
}
```

### Velocity After Dropping
When an object is dropped, the holding [[Node]]'s position/rotation and lastPosition/lastRotation should be used by the server to calculate the velocity/rotationalVelocity of the Object.

### Creating 
URL:
```json
{
	"type":      "createObject",
	"modelType": "URL"
	"model":     "https://www.example.com/object.tar.xz"
}
```
TAR.XZ BASE64 block:
```json
{
	"type":      "createObject",
	"modelType": "BLOCK"
	"model":     "VEFSLlhaIEJBU0U2NCBCTE9DSwo="
}
```

Both return an Object ID.

### Listing Objects
```json
{
	"type": "listObjects"
}
```
Returns a vector with all Object IDs.

### Retrieving Attributes
```json
{
	"type":   "retrieveObjectAttributes",
	"object": "objectID"
}
```
Returns a dictionary/map containing all Public attributes of the Object.