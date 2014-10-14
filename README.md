blastbuster-vr
==============
The Game for LEAP Motion VR Mount 

Teaser site
http://www.circle-hydrangea.net/perilous-dimension-english/

Method:
Leap Motion's easy method to get 2D-position is interactionBox.NormalizePoint()
However, it coordinate is different from a pass-through image.
Therefore I acquire the coordinate of the fingertip edge using the next method.

```cs
  GameObject[] fingerTips = new GameObject[10];
  Frame frame = controller.Frame();
  Vector3 pos = frame.Hands[x].Fingers[y].Bone(Bone.BoneType.TYPE_DISTAL).NextJoint.ToUnity(HandController.mirrorZAxis);
  fingerTips[i].transform.localPosition = pos;
  fingerTips[i].transform.LookAt(camera.transform.position);
```
And I confirm whether a finger-tip covered up a target with a viewport coordinate.
```cs
  Vector3 shootPos = camera.WorldToViewportPoint(fingerTips[i].transform.position);
  Ray ray = camera.ViewportPointToRay(shootPos);
```

Contacts
- twitter: @yasei_no_otoko
- facebook: haruto.watanabe.3
- email: circle.hydrangea@gmail.com

© 2013 Haruto Watanabe
