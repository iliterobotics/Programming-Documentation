### Variables
- Constants
    - Preceded by `k`
    - First word should be the name of the subsystem the constant is for
    - Ex: `kDriveLeftRearTalonId`, `kLimelightFov`, `kControlLoopPeriod`
- Fields
    - Preceded by `m`
    - Fields are any variables found in the **class body**
    - Ex: `mWristAngle`, `mGyroAngle`
- Parameters
    - Preceded by `p`
    - Ex:
    ```
        public DriveStraight(Drive pDrive, double pDistanceToDrive) {
            mDrive = pDrive;
            mDistanceToDrive = pDistanceToDrive;
        }
    ```

### Constructors
- If your class needs to use another classes' object, it should be passed into the constructor
- Settings that are essential to your code's functionality (like the number of degrees to turn for `GyroTurn`) can also be passed in

### Setting Properties
- If you need to override a default setting for a class, use the flow model
- Ex: To override the default power sent to the drivebase in the `DriveStraight` command:
```
public DriveStraight setPower(double pPower) {
    mPower = pPower;
    return this;
}
```
- This allows us to create a `DriveStraight` object like so:
```
ICommand = new DriveStraight(mDrive, 10.0 /*The distance to drive*/).setPower(0.5);
```

### Enumerations
- Enumeration classes are in
- Enumerations are in all caps, `LIKE_THIS`
- The rationale behind this naming scheme is that Codexes (which rely on enums) will eventually be sent from the robot and
deserialized into a database - and database column names are typically in all caps.
- Ex: States of a manipulator:
```
public enum EManipulatorState {
    RESET, GRABBING, PLACING;
}
```
