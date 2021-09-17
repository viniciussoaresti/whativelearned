# SCRUM:

"Scrum is a framework that helps teams work together. Much like a rugby team (where it gets its name) training for the big game, scrum encourages teams to learn through experiences, self-organize while working on a problem, and reflect on their wins and losses to continuously improve", [Atlassian](https://www.atlassian.com/agile/scrum).

## Traditional Development (Waterfall) vs Agile Development

![Traditional vs Agile](https://res.cloudinary.com/monday-blogs/w_881,h_501,c_fit/fl_lossy,f_auto,q_auto/wp-blog/2020/12/pasted-image-0-31.png)

Thus, delivering value to the stakeholders since the first deploy, not only on the final iteration.

## Team:

- Product Owner (PO): has knowledge of the business rules, and translates from the stakeholders to the development team what needs to be done and validates the sprints outcome.

- Scrum Master (SM): incentivizes the correct usage of SCRUM, and solves issues between the PO -> DEV TEAM communication, aiming at the team to be completely independent in the future.

- Development Team: design, programming, testing, and all that's necessary to develop the required functionalities.

## Ceremonies:

- Sprint: time box where some tasks are scheduled to be done. Inside sprints, some other ceremonies happen: sprint plannings, daily meetings, sprint reviews and sprint retrospectives.
    - Sprint Planning: the PO explains what is expected to be done on the sprint, and details all tasks. After that, the development team splits the tasks and define how much effort is required to do each one. One of the methods for doing that, for example, is the famous "planning poker";
    - Daily Meeting: Quick meeting between all parties (PO, SM and DEV), explaining what was done yesterday, what is going to be the goal for today, and bringing up some troubles or concerns that may exist;
    - Sprint Review: On the sprint's last day, the DEV team presents all work done to the PO;
    - Sprint Retrospective: Also on the last day, all parties are (or should be) transparent and bring up some problems that occurred, what was done to solve it, and what could avoid the same problems on the next sprints.

## Tasks:

Commonly, the tasks can be divided like this:

- Epics: the main summarized goal expected to be added to the product, for example, "the creation of the cart page", for an eCommerce.

- Stories (on Azure DevOps called Issues, for example): user's desired functionalities inside the epic (therefore, the epic's details), and/or business rules, describing what the system should do. For example: "user can add the necessary items in his cart".
    - It's great if the story has some clear boundaries between front and back-end rules, has some screen sketches, KPI's (Key Performance Indicators: what are some metrics that are able to define if the story is achieved inside the application), and such. 

- Tasks: what should be done to make the stories happen. For example: "add the page and the link 'cart' on the main website page" and "add the button remove item from cart after every item".