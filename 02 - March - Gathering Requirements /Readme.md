Notes From "Its all about Requirements and Planning"

* Excercise 1 PB&J: Break off into teams and give me a specification. 

* 15 Minutes: Study Music

* 3 teams will read off their directions and I will make them.

* Summize what we talked about last time brining up people that were not there.
	* Remember the six pillars to success
		1. Learning
		2. Failure	
		3. Networking
		4. Dedication To the Craft
		5. Self Improvement and Feedback
		6. Teamwork

	* By tonight you will have practiced all six, because tonight we are going to talk about the Software Development Lifecycle and focusing specificially on Requirements and Planning.

* Why?
	* [Failure!](http://faethcoaching.com/it-project-failure-rates-facts-and-reasons/)
	* Things fail and if you don't plan then they fail more often, projects need some way to formerly design and figure things out. That is what you are paid to do -- to figure out the system, how it needs to work, how it needs to function. To ask clarifying questions to be sure that you truly understand the problem. If you do not understand the problem, then you can not solve. it. 

* So what is the SDLC?
	* SDLC is the acronym of Software/System Development Life Cycle aka as Application Lifecycle and Product Lifecycle. It is also called as Software development process. The software development life cycle (SDLC) is a framework defining tasks performed at each step in the software development process. [Source](http://www.tutorialspoint.com/sdlc/sdlc_overview.htm)

	* Characteristics of SDLC
	* ![](http://www.tutorialspoint.com/sdlc/images/sdlc_stages.jpg)
		* Prelim analysis - Conduct a study to see if its feasible and what problems this solves/causes. Risk analysis could be done here to detemine the feasibility of the system and if it costs outweigh its benefits. We are going to be looking at this in depth
		* Systems analysis, requiremtns definition: We gather and interpet facts this can be through meetings (ugh!), questionaires, looking at existing systems or other metrics that can be obtained (analytics, test reports, etc)
			* Steps
				*	Collect Facts
					* Ask questions,
					* Collect existing information
					* formalize a hypothesis
					* Test 
				* Scrutizinize existing system - Identify pros and cost of current system in place. For example rewrites, we want to fix without reintroducing the problems that were initially in the old system. You also may determine that fixes can be implemented in existing system to satisfy requirements and pain points.
				*  Analyze the propsed system: Come up with solutions to shortcomings in existing system.
		* Systems design: Describe featueres and operations in detail, including screen layouts, bussiness rules, process diagrams, psuedocode and other docs -- these other docs could be support documents that illustrate why you need to make these changes. This will help develop use cases.
		* Develop - You write code at this point
		* Integration and testing - Brings all the pieces together into a special testing environment, then checks for errors and bugs.
		* Acceptence, installationa nd deployment: You deploy this to production
		* Maintenance: System is in production you have to maintain it, you add new code, remove unusued features, add new mini architectures. 
		* Disposal: When the system reaches it's EoL its disposed, and a new system is used that goes through all the steps the old system did. 
	* Now this all sounds very waterfally but here is the crux of that matter, all development follows sometype of outline like this, wheater you are doing BDUF (Big Design Up Front) or you are doing incremental development (Agile). The reason we go through these stages is because you have to *DESIGN* what to build before you *BUILD* it or *ELSE* you will *BUILD* the wrong solution.
	* ![Project Methodolgies](http://blog.digite.com/wp-content/uploads/2014/09/Requirements-management.jpg)
		
	* Depending on the methodology this could be circular as in goes on forever, or linear. 
		* Iterative (Small Circles)
			![Iterative](http://www.tutorialspoint.com/sdlc/images/sdlc_iterative_model.jpg)
			* This can work for things were change has to be driven and the risk of not changing means that you become a slain victim of your competition. 
			* The business demands change at a frequency greater than a water fall system would be
			* Examples:
				* Websites: This is pretty self explanatory
				* Software Services: Api's have to change, your customers will demand new features and you have to be able to satisfy those changes.
				* Business Desktop Applications: The business will demand changes, and if those changes can give the departments an added advantage or overcome a requirement that is imposed by a regulatory requirement then the better. 	
				
		* Linear
			* This is for big projects where risks and procedures have to be well clarified. Or you can't build something while its in production
			* examples:
				* NASA:  	The Apollo Missions, software, hardware and other items. You can't patch software when the application is required for all health systems and guidence systems for a crew of 3.
				* Medical Systems: While some things can be hot patched its __more__ important that things work and go through a series of tests and benchmarks to ensure that the system works at all times. There is no sympathy for critical systems for errors when they do not work. Think about it, would you want a cavelier attitude like agile to be in place where people's lives are at stake?
				* Critical Automation Controls: Software to change on devices like Monitoring systems for environmental controls are slow to change, they go through very rigorous testing, because money is at stake.
		
			![](http://www.tutorialspoint.com/sdlc/images/sdlc_waterfall_model.jpg) 

		* Let me be clear that no matter what methodology your team uses, the steps are pretty much the same, the cadence is just different. 
			* If its liniear then you do these one activity at each stage of the project
			* If its non-linear then you do each activity at each sprint.

	* Before breaking ground on a new system
		* You have to evaluate if the new system makes sense to build, you can do this via interviews with the customer or maybe they have made the determination that the old system is insufficent or that this is an entirely new system or workflow. 
		* So the first thing you do is interview the stake holder and find out what first, what is the current workflow. All systems have a current workflow, whether it's manual or whether its  a product they have or something that was built. You have to do some sleuthing and speak to people. This is very difficult ground to be treading on, because some people do not understand you can not design a solution unless you know the problem. 
			* Uncovering questions to ask: Depending on who is the inhouse expert or SME (Subject Matter Expert) we are going to have questions to clarify the solution. Lets start with something outside of software.
				* Customer comes in and says "I want a cake"
				* True or false: is that enough info to actually start baking the cake?
				*  The customer or stake holder will want something specific, and has something in mind. But unless you are telekenetic you are going to have difficulty getting to what that ideal is. That is why its important we ask questions about the properties of the cake. These are called requirements.
			*  So we have identified that asking for a cake is not enough to start baking the cake. How can we get started on that cake?
			*  We ask questions: We conduct an interview, like what type of cake do they like, what is the ocasion of the cake, what is amount of people this cake has to be able to serve. We have to ask questions to get to this information, and then we can more or less see what the customer actually wanted. 
		*  We can refer to these properties as Functional Requirements: 

>> In software engineering (and systems engineering), a 
>> functional requirement defines a function of a system 
>> and its components. A function is described as a set 
>>   of inputs, the behavior, and outputs (see also
>> software). Sounds like this [https://www.youtube.com/watch?v=pZiv8vkxMac] is not this [https://www.youtube.com/watch?v=VaT7IYQgyqo]

### This is where you get to do some sleuthing

	

* Let them eat cake If the person comes in saying they want.
	 * A cake for a Birthday for a child, and they want it taste like cookies and creme and white white and yellow frosting and it needs to serve about 20 individuals, do you have enough data to proceed making the cake?
	 * YES! You may still have to ask some clarifying questions but enough data is present to actually make a cake order and to process the order.

* Usually in software, a customer has a vauge idea of what they want. They mostly don't care how you get there, unless they are in technical. For example a customer that asks for say like a order entry form, could care less what technology you use, they care more about the form and function of the site or application. However, if you have a customer that is asking for a interface to upload data to a webservice, they probably care at least at some layer how you transmit the data. For example depending on the environment a customer in retail would probablly prefer to transmit the data via batch jobs or directly via a call to a remote RPC service, a consumer via the web would probally want an interface exposed over HTTP.

* Other Disasters Because of Bad Requirements and Subjectiveness using realtive terms.

[http://www.cnn.com/TECH/space/9909/30/mars.metric.02/]
[https://www.youtube.com/watch?v=tWc4gGMQ3hQ]

* Mock interview: Lets practice what we have learned. I am going to play the client and you guys are going to play the engineer, i have a vauge idea of what i want. You need to guide me to get what i want. I want you to use a piece of paper to convey the idea. This is called wireframing. You can ask me questions and I may give a vauge answer or not.

* We need a solution to allow customers to get coupons.
* Go!

* Excercise II: Think about this, I want you to write requirements for a traffic light. Think back to knowing what you know about the PB&J excercise.



* Play list 2:

* Go over requirements people have deducted.

* Requirements can lead into visual documents usually SRS (Software Requirements Specification) this is a document that describes in detail what the software needs to do. Going back to the coupons example, you would write a requirement for all use cases that you have identified and expand, this would include mockups of how the system would work, this would include notes from meetings from your customer and clients and justifications for the solution from a business and techical end. This would be the document that the architect or senior lead can start coming up with the technical requirements, or architecture document that the team can use to drive the project forward. 
* These documents the architect come up with are the Technical Specifications that the team will use, they will include diagrams and blue prints for objects that are talked about, they will include the how to implement the specification and also go into painful detail on how to think of the system as a whole. They will also be what are used to uncover the non-functional requirements of a system.

>In systems engineering and requirements engineering, a non-functional requirement is a requirement that specifies criteria that can be used to judge the operation of a system, rather than specific behaviors. They are contrasted with functional requirements that define specific behavior or functions.


* Non Functional Requirments
	
	* Non functional requirements describe how the system will handle technical requirements, for example Security can be a non-functional requirement. Its not something that lends it self to the function of the system but a requirement to the system. Load balancing can also be a non functional requirement in addition to speed and load, these are just a few examples of nonfunctional requirements. We have to identify these from the requirements that are obvious functional requirements and speak with the business group or product owner on what is considered acceptable. For example, perhaps they say that its vitally important that a user has to be secure when loggin in. This would uncover a fact that security is very important when it comes to logon functions or account functions in general. Perhaps they also so that to be competitive we need to have page times that are small as possible, this creates a non functional requirement for a caching system where data does not have to be transactionally correct. For example a landing page or a products page, it could also uncover that it could be OK for a item to say its in stock on one page but when the user goes to put hte item in the cart its out of stock.


* Lets think about the traffic light examples, what are some non functional requirements that may not be so obvious?

  





			
			