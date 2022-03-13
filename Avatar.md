### Terms
- Avatar: The models that users control

### Attributes
- avatarName: Name of the Avatar. Specified in [[Auth]] request.
- position: `Vec3`; {xPos: int, yPos: int, zPos: int}; Stores the position of the avatar.
- lastPosition: `Vec3`; {xVel: int, yVel: int, zVel: int}; Stores the previous position of the avatar; Used for calculating velocity of avatar (and anything a client or server might need it for, such as collisions). 
- rotation: `Vec3`; {xRot: int, yRot: int, zRot: int}; Stores the rotation of the avatar.
- lastRotation: `Vec3`; {xRVel: int, yRVel: int, zRVel: int}; Stores the previous rotation of the avatar.

### Setting
Avatar models can be set or reset with a "setAvatar" request:

##### With a URL:
```json
{
	"type":      "setAvatar",
	"modelType": "URL",
	"model":     "http://www.example.com/path/to/model.tar.xz"
}
```
##### With a XZ compressed BASE64 block:
```json
{
	"type":      "setAvatar",
	"modelType": "BLOCK",
	"model":     "QkFTRTY0IFRBUi5YWiBGSUxFCg=="
}
```

### Updating Position & Rotation
```json
{
	"type":     "avatarUpdate",
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
	"type":   "retrieveAvatarAttributes",
	"avatar": "avatarName"
}
```
Returns a dictionary/map containing all Public attributes of the Avatar. Not specifying avatar should retrieve the attributes of the client's avatar.