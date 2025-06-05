# Activity 4  
**Chris King**  
Grand Canyon University  
SDD-630 Mobile Software Development  
Professor Estey  
June 4, 2025 

---

## **Activity 4.1 – Applying the Hook Features**

To improve user loyalty for Project TARS, I will incorporate specific features aligned with Nir Eyal’s Hook model: **trigger**, **action**, **variable reward**, and **investment**.

### **Trigger**
The most common trigger will be push notifications inviting users to interact with TARS. Notifications can be dynamically assigned to users based on their account subscriptions. For example, if a user has a subscription which allows access to a variety of new models, notifications can be pushed to invite the user to try models that they have not yet explored. If a user has not tried any Tests, notifications can invite them to try their first Test to earn points torwards a new model.

### **Action**
The core action, drawing a digit, is already simple, but can be improved further by introducing:
- One-tap canvas reset button    
- Onboarding overlays for new users  

This reduces friction and aligns with Eyal’s principle that the action must be “easier than thinking.”

### **Variable Reward**
When a user submits a drawing, the neural network will respond with an animated interpretation. For educational purposes, a "Test" system can be added. When the "Test" session is started by the user, a random neural network will be generated depending on the model the user selects. For example, for digit recognition, a Spiking, Convolutional, or Multi-layer neural network may be generated. The user can draw different digits to see how the neurons and synapses fire, and try to guess what kind of neural network it is. These model varieties will be temporary and only available in "Test" mode. However, points earned from completing tests can be used in an in-app "Shop" to purchase model varieties permanently.

### **Investment**
We will add a user profile that tracks:  
- Personal best scores for "Test" mode accuracy  
- Total points acquired
- In-game achievements, such as "Purchase your first subscription", or "Complete Five Tests for Natural Language".  

By investing time into building their profile, users grow more attached and are more likely to return.

---

### **Hook Framework Mapping**
| Hook Step         | App Feature                                      |
|-------------------|--------------------------------------------------|
| Trigger           | Daily challenge notifications                    |
| Action            | Drawing digits on an optimized canvas            |
| Variable Reward   | Animated model feedback and point acquisition     |
| Investment        | Saved profiles, progress streaks           |

These improvements complete the Hook cycle and build long-term engagement while maintaining the app’s educational purpose.

---

## **Activity 4.2 – Morality of Addicting Products**

While our app’s goal is education, overuse, especially among students or hobbyists, is a legitimate concern. Guided by a Christian worldview and supported by responsible design, we will proactively discourage unhealthy usage patterns.

### **Potential Addictive Behaviors**
- Repeating challenges excessively to manipulate model behavior  
- Obsessing over leaderboard or accuracy stats  
- Spending long, unbroken sessions on visualization  

As Nir Eyal notes in *"Is Some Tech Too Addictive?"*, products must be designed with ethical limits and user wellbeing in mind.

### **Healthy Use Guidelines**
- **30 minutes/day** for casual learners  
- **1 hour/day** max for educators or classroom use  
- Reminders after 30 minutes of use: “Take a quick break—your brain will thank you”  

These recommendations are rooted in Christian wisdom, honoring rest, moderation, and mental stewardship.

### **Design Safeguards**
- **Session timer** to track daily time  
- **Intent prompts**: “What do you want to learn today?”  
- **Break encouragement** after challenges: “Let’s pick this up tomorrow”  

Stack Overflow limits excessive reputation farming for similar reasons, balancing growth with sustainability. Our app will do the same by reinforcing healthy engagement boundaries.

### **Christian Worldview Response**
Scripture encourages self-control and wise use of time (Ephesians 5:15-17). We believe education should empower, not enslave. By clearly communicating limits and prioritizing meaningful learning over addictive loops, we help our users grow without compromising their wellbeing.
