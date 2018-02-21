# RUBRIC

### The Model

  The state of the car is represented by x,y,v,psi,cte and epsi which are the x position,
  y position, velocity, the angle between the heading of the car and the fitted poly, the
  cross track error and the error in the angle respectively.
  The acutators are the acceleration of the car and the steering value.
  The update euations are the kinematics equations of motion.

### Timestep Length and Elapsed Duration (N & dt)

  N is the number of time steps while dt is the time between acutatations, multiplied
  together they give the prediction horizon which is the duration over which future
  predictions are made.
  T should be as large as possible, while dt should be as small as possible. However,
  when I tried to put a big value for N the solver became very slow and the car crashed.
  Previous tested values for N where 50 and 30, but 10 gave the best results.

###Polynomial Fitting and MPC Preprocessing

  The only preprocessing done here is transforming the x and y waypoints to the car
  coordinates through translation and rotation before fitting a polynomial on them which
  made computing the predictions easier.

###Model Predictive Control with Latency

  Latency was handeled by predicting what will the state of the car be after the time given by
  the latency and then passing this new state to the solver of the MPC to work with
  as this state will be the actual state of the car at the time the acutators are 
  applied.  