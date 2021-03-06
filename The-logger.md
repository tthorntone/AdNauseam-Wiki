[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

AdNauseam comes with a logger (based on the uBlock Origin logger), which gives the ability to inspect what AdNauseam is doing with network requests and DOM elements, whether something is blocked or allowed, and which filter, if any, matched a network request or DOM element.

The logger is the tool of choice to see, understand, diagnose and fix the functioning of AdNauseam.

To access the logger, first click the uBlock button in the menu, then select the logger icon:

![Figure 1](https://user-images.githubusercontent.com/4967860/117322505-5b94ce80-ae8e-11eb-8f27-10304a9cd321.png)

![Figure 2](https://user-images.githubusercontent.com/4967860/117322598-6f403500-ae8e-11eb-985a-6b3f33d32c9b.png)

The request logger will open in a new tab:

![Figure 3](https://user-images.githubusercontent.com/4967860/118269692-57d0ff80-b4bf-11eb-968e-3651c04272d2.png)

Note that AdNauseam will log entries **IF AND ONLY IF** the logger is opened. Otherwise, if the logger is not opened, no CPU/memory resources are consumed for logging.

Logger events in AdNauseam are color-coded for easy identification, as follows:


![Figure 4](https://user-images.githubusercontent.com/4967860/118269253-ccf00500-b4be-11eb-9c64-ddadef91d6d2.png)

You can find more information on the original uBlock logger [here](https://github.com/gorhill/uBlock/wiki/The-logger)...

***
