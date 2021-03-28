


## What is Kalman Filter?

The Kalman filter is an algorithm that uses noisy observations of a system over time to estimate the parameters of the system and predict future observations. Note that some of systems are unobservable. At each time step, it makes a prediction, takes in a measurement, and updates itself based on how the prediction and measurement compare.

The algorithm is as follows:

Take as input a mathematical model of the system, i.e. the transition matrix, which tells us how the system evolves from one state to another.  Alternatively, if we have a system which is fairly stable, we might model its evolution as a random walk. If you want to read up on Kalman filters, note that this matrix is usually called A. the observation matrix, which tells us the next measurement we should expect given the predicted next state. The control factors are summarized in a matrix B with time-varying control vector u, which give the offset Bu. covariance matrices of the transition noise (i.e. noise in the evolution of the system) and measurement noise, denoted Q and R, respectively. Take as input an initial estimate of the state of the system and the error of the estimate, a and b. At each timestep: estimate the current state of the system x using the transition matrix take as input new measurements z use the conditional probability of the measurements given the state, taking into account the uncertainties of the measurement and the state estimate, to update the estimated current state of the system x and the covariance matrix of the estimate P. This graphic illustrates the procedure followed by the algorithm.

It's very important for the algorithm to keep track of the covariances of its estimates. This way, it can give us a more nuanced result than simply a point value when we ask for it, and it can use its confidence to decide how much to be influenced by new measurements during the update process. The more certain it is of its estimate of the state, the more skeptical it will be of measurements that disagree with the state.

By default, the errors are assumed to be normally distributed, and this assumption allows the algorithm to calculate precise confidence intervals. It can, however, be implemented for non-normal errors.

