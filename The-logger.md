[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

AdNauseam comes with a logger (based on the uBlock Origin logger), which gives the ability to inspect what AdNauseam is doing with network requests and DOM elements, whether something is blocked or allowed, and which filter, if any, matched a network request or DOM element.

The logger is the tool of choice to see, understand, diagnose and fix the functioning of uBlock.

To access the logger, first click the uBlock button in the menu, then select the logger icon:

![Figure 1](https://raw.githubusercontent.com/wiki/dhowe/AdNauseam/logger.png)

The request logger will open in a new tab (which was moved to its own window below):

![Figure 2](https://raw.githubusercontent.com/wiki/dhowe/AdNauseam/logger-lines.png)

Take note that the network request logger in uBlock is a forward-looking logger: this means only future requests can be logged.

In the spirit of efficiency, AdNauseam/uBlock will log entries **IF AND ONLY IF** the logger is opened. Otherwise, if the logger is not opened, no CPU/memory resources are consumed by uBlock for logging purpose.

***
