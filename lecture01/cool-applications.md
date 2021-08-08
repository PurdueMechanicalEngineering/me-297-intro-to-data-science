(data-science-me-applications)=
# Some cool appliations of data science in mechanical engineering
What follows is an incomplete list of cool things that one can do combining
mechanical engineering with data science. Note that these applications are
rather advanced. We will not learn how to carry them out in this class. You
will, however, learn the fundamentals upon which the data science components of
these applications are based.

(space-x-falcon-landing)=
## Space X Falcon rocket landing
Space X uses a particular data science technique called
[Kalman filter](https://en.wikipedia.org/wiki/Kalman_filter#:~:text=In%20statistics%20and%20control%20theory,than%20those%20based%20on%20a) 
to estimate the position and velocity of the Falcon rocket using noisy data
coming from GPS and accelerometers. The characteristic of this technique is that
it quantifies the uncertainty in the estimate. Once the estimate is available,
then we can decide which thrusters to activate to control the rocket as desired.

<iframe width="500" height="281" src="https://www.youtube.com/embed/l5I8jaMsHYk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

(boston-dynamics)=
## Boston Dynamics spot autonomous navigation
Spot is a dog robot. Spot also uses the Kalman filter to localize itself in
space. Here is the description of the video: "Spot autonomously navigates a
specified route through an office and lab facility. Before the test, the robot
is manually driven through the space so it can build a map of the space using
visual data from cameras mounted on the front, back and sides of the robot.
During the autonomous run, Spot uses data from the cameras to localize itself in
the map and to detect and avoid obstacles. Once the operator presses 'GO' at the
beginning of the video, the robot is on its own. Total walk time for this route
is just over 6 minutes."

<iframe width="500" height="281" src="https://www.youtube.com/embed/Ve9kWX_KXus" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

(extra-terrestrial-habitats)=
## Smart extraterrestrial habitats
The [Resilient Extraterrestrial Habitats Institute (RETHi)](https://purdue.edu/rethi/?_ga=2.219727577.1509543321.1624260470-1305845852.1623658385) is a NASA-funded
project based at Purdue the vision of which is to develop technologies that
enable the design of habitats on the Moon and Mars. These structures will likely
remain without crew for significant periods of time ranging from months to years
making autonomy a key requirement.
[Prof. Bilionis](https://www.predictivesciencelab.org) is leading the Awareness
Thrust of the institute. The Awareness Thrust is responsible for developing data
science technologies for assessing the health state of all habitat systems using
sensor data and controlling robotic agents to carry out maintenance and repair
activities. Note that every year there are various opportunities for
undergraduate research on data science related topics at the institute. In the
video you will see [Prof. Dyke](https://engineering.purdue.edu/IISL/), who is
leading the project.

<iframe width="500" height="281" src="https://www.youtube.com/embed/yFd8wE9qtkw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

(virutal-surgery)=
## Virtual surgery
[Prof. Buganza](https://engineering.purdue.edu/tepolelab/) combines physical
models of skin with data collected from patients and experiments to simulate
skin surgeries. In the process, he has to solve parameter calibration problems,
quantify uncertainties in skin properties, and propagate these uncertainties
through the physical models.

<iframe width="438" height="415" src="https://www.youtube.com/embed/lOl_tPj9sMs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
