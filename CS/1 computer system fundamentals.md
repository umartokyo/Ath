2024/08/28, #computer-science #notes #sumire #umarik 
## 1.1.0 System Life Cycle
System life cycle refers to the stages of software's life.
- Initial concept to eventual retirement.
- Used to ensure that a system meets required needs and effectively managed through its life cycle.

Example system life cycle:
	Analysis → Design → Implementation → Operation → Maintenance
Software life cycle:
	Planning and Analysis → Design overview → Development → Evaluation
## 1.1.1 Systems in organizations
### Lexicon:
**Context**: environment, condition, needs
**Stakeholder**: anyone who is relevant in the process
	define problem / opportunity
**Extent**: Defined capabilities, what it can do? (functionalities, problems to solve, user needs)
**Limitation**: Constrains. (scalability, applicability, performance, technical, financial)
### Planning
A new system can be created or obtained in order to gain some benefits from the newer system. While planning and installing the software is a problem of its own to be solved, there is a high possibility of other problems to arise like lack of stakeholder participation, lack of attention to proper training and so on. To ensure a good system change, feasibility report / study must be conducted, which evaluates the project and gives insights on its operation.

**TELOS**: (feasibility study / report)
**T**: Technical feasibility; is the existing technology sufficient?
**E**: Economic feasibility; is it cost effective?
**L**: Legal feasibility; are there any conflicts with legal systems? is it ethical?
**O**: Operational feasibility; existing operational systems to support maintenance?
**S**: Schedule feasibility; existing operational systems to support maintenance?

Case:
	New system in Japan to enhance urban traffic using AI powered traffic signals.
	- Takes time to integrate, legal concerns for data protection.
## 1.1.2 Need for change management
Successful change management ensures that all stakeholders embrace the change.

Social / Ethical issue:
- Structured approach to transition groups to desired future state
- Managing human side → addressing resistance

Case:
	New customer relationship management system (CRM system) → concerned sales team adaptation with no time for training so they just give out manuals for self-study at home. (very bad idea)

### Organizational Issues
- **Change management**: Managing resistance to change. (training to use new system)
- **Training & Support**: Providing adequate resources and ongoing support.
- **Resource allocation**: allocating sufficient resources, including time, budget, personnel.
- **Integration with existing systems:** Ensuring the new system integrates smoothly with existing systems.
- **Communications**: Maintaining clear communication throughout. (frequent communication with client is necessary)

Case:
	UK NHS (health) → Lorenzo system → centralize patient records
	Issue: integration & user adaption
	Administration: telephone numbers, emergency contact


HW: [[CS Flashcards]]
## 1.1.3 Compatibility issues
**Software Incompatibility**: When software cannot operate cooperatively.
**Compatibility**:  The ability of different systems, devices, components to work together effectively without conflicts or issues.
- hardware and software applications can operate seamlessly with each other
- so that various elements within a system can interact and perform as intended
- example: bank account →wider range of audience (customer satisfaction)

**Legacy Systems**:
- an older computer system that remains in use despite being outdated
- can pose challenges for integration, security and scalability but sometimes retained due to high cost or complexity of transitioning to the new systems.

**Business Mergers**: Strategic processes where two companies combine to form a single entity.
- goals: expanding market reach, increasing operational efficiency, enhancing competitive advantage
- consider: international dimension & social / ethical issue
- integrate resources, operations cultures → aligning business strategies, systems, personnel

**4 Strategies for integration**:
1. Keeping both systems and develop same functionality. (expensive)
2. Replace both systems with something new. (increased initial cost)
3. Pick better parts of each company's systems. (difficult)
4. Better system out of two is selected. (policy problems)
## 1.1.4 Different system implementations
Business software can be either locally or remotely hosted.
**Locally hosting**: Better for larger and complex systems.
**Remotely hosting**: Better for high hardware requirements or need of outsourcing the maintenance.

Modern version of 'Software as a Service' (SaaS) is often referred to as 'Cloud-Native Services'. They are designed specifically for cloud environments, leveraging cloud computing's scalability, flexibility, and distributed architecture. 

SaaS features:
**Advantages**: Low initial costs, few investments for installation, maintenance and upgrading.
**Disadvantages**: Subscription basis, less secure, scalable, internet requirement.

SaaS vs Cloud
- traditional SaaS → server fails = can't do anything
- cloud-native application → serverless → can continue to use
- SaaS example: Salesforce, Dropbox, Zen disk
- Cloud example: Spotify, Netflix, Zoom
## 1.1.5 Alternative installation processes
**Changeover**: Process of putting the new system online and retiring the old one.
Installation of a new system is a pretty frequent process. You have to choose one of the changeover methods to balance between cost and risk trade-off.

**Types of Changeovers**:
1. Parallel
	Running both old and new systems for some period of time.
	Advantages: Helps to compare old and new systems in action.
	Disadvantages: Costly, often systems are irrelevant.
1. Big Bang / Direct
	Old system is replaced with new one immediately.
	Advantages: Cheap, fast.
	Disadvantages: Risky, users must be trained before system integration.
1. Pilot
	Update system for one group from the company and if it they like it, spread it.
	Advantage: Low Risk.
1. Phased
	Update a system module by module.
	Disadvantage: Longer training period.
## 1.1.6 Problems of data migration
Transfer of data from older software to the newer one has some risks and challenges to overcome. The chance of data incapability, non-recognizable data structures, loss of data, or incomplete data transfer are non-zero and can lead to errors during the process.

**Data Migration Stages**:
1. Plan
2. Migrate
3. Validate
## 1.1.7 Various types of testing
loading...