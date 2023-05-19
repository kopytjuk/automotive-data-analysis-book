# Implementation in Python

The concepts mentioned above and the conversions between various systems (together with a TF-tree) are implemented in [`pytransform3d`](https://github.com/dfki-ric/pytransform3d):

```python
# from: https://github.com/dfki-ric/pytransform3d#example

import numpy as np
import matplotlib.pyplot as plt
from pytransform3d import rotations as pr
from pytransform3d import transformations as pt
from pytransform3d.transform_manager import TransformManager


rng = np.random.default_rng(0)

ee2robot = pt.transform_from_pq(
    np.hstack((np.array([0.4, -0.3, 0.5]),
               pr.random_quaternion(rng))))
cam2robot = pt.transform_from_pq(
    np.hstack((np.array([0.0, 0.0, 0.8]), pr.q_id)))
object2cam = pt.transform_from(
    pr.active_matrix_from_intrinsic_euler_xyz(np.array([0.0, 0.0, -0.5])),
    np.array([0.5, 0.1, 0.1]))


tm = TransformManager()  # holds the TF tree
tm.add_transform("end-effector", "robot", ee2robot)
tm.add_transform("camera", "robot", cam2robot)
tm.add_transform("object", "camera", object2cam)

# holds the final transform matrix
ee2object = tm.get_transform("end-effector", "object")
```

## References

[^rotation-formalisms-wiki] Wikipedia - [Rotation formalisms in three dimensions](https://en.wikipedia.org/wiki/Rotation_formalisms_in_three_dimensions)

[^davenport-rotations-wiki] Wikipedia - [https://en.wikipedia.org/wiki/Davenport_chained_rotations](https://en.wikipedia.org/wiki/Davenport_chained_rotations)