# Activity 1  
**Chris King**  
Grand Canyon University  
SDD-630 Mobile Software Development  
Professor Estey  
May 14, 2025  

## Introduction
Project TARS is an ongoing capstone initiative that began as part of my undergraduate studies and has since evolved into the centerpiece of my graduate work. At its core, TARS is an interactive AI platform that allows users to communicate with a custom-built neural network. [The original version of TARS](https://github.com/Sasqe/TARS) is a language model that is deployed on a Raspberry PI, exposed by an API server through WiFi. Since then, TARS has been evolving to live in the cloud, with various user interface tools that can be used to communicate with it. This brings about an excellent opportunity to design a mobile user interface for TARS.

Rather than focusing on the technical backend or deployment details, this version of TARS will emphasize user experience and mobile-first accessibility. The goal is to bring the power and personality of TARS into a mobile interface that feels intuitive, visually engaging, and deeply connected to the user. Over the course of this project, I’ll be detailing the app's design, its ideal audience, and how it stands apart in the current market landscape.

## Ideal User Profile 

The ideal user for TARS is a student, hobbyist, or aspiring machine learning engineer who wants to truly understand how neural networks think—not just at the code or model level, but visually and interactively. These users aren’t satisfied with just reading output predictions or metrics on a dashboard. They want to *see* what's happening inside the model: how input flows through the layers, how neurons and synapses activate, and how each part of the network contributes to the final decision. Many of them are visual learners, and the abstract nature of neural networks often becomes a barrier when there’s no intuitive way to break down what’s going on under the hood.

The core problem these users face is the lack of transparency and real-time visibility into the workings of neural networks. Tools like [TensorBoard](https://www.tensorflow.org/tensorboard) exist, but they’re either too technical, too static, or don’t offer the kind of live, tactile interaction these users crave. TARS bridges that gap, offering a neural network that doesn't just perform, but teaches, shows, and responds visually as it processes information. It makes the “black box” a little less black.

## Solution Design

The TARS mobile app solves the problem by turning an abstract concept, how neural networks function, into a dynamic, real-time experience. When a user sends input into the app, TARS doesn’t just return a prediction. It animates the neural network’s entire process from input to output. Neurons light up, layers activate in sequence, and weighted connections pulse to reflect computational intensity. The user gets to visually trace the model’s reasoning as it happens.

TARS is intentionally designed to feel more like a companion than a sterile tool. Every interaction is met with a fluid response, whether it’s a fluid animation when drawing on the canvas or a soft glow spreading across a fully activated layer. This isn’t just for aesthetics; it reinforces learning by tying visual feedback to data flow.

The app’s layout is minimal and focused. The screen simply shows the "dead" neural network at first, with no neural activity. When the user holds down on the screen, The transparent drawing canvas appears over the screen cleanly with subtle visual cues to guide interaction. Once the user is finished drawing, the canvas fluidly disappears to display the neural network beneath, lighting up as it processes the input. A custom-built software component called "AI Captioning", or "Bot", will display a message somewhere on the screen when the processing finishes, containing TARS' answer in natural language. The neural activity will also continuously loop until the user sends another message, allowing the user to analyze the flow of the neural activity for as long as they need. 

![TARS Wireframe](<tars-wireframe2.drawio (1).png>)

In addition to the core visualization, TARS offers in-depth interactivity, where users can tap on individual neurons or synapses, and view details like activation values or gradient flow (simplified for accessibility). This transforms the experience from passive observation to hands-on exploration, giving users a much deeper sense of how machine learning models actually think. The neural network is also a three-dimensional model in a three-dimensional space, which allows the user to zoom in and out, as well as rotate the neural network to view it from different angles. 

## Comparison Research

There are a few existing tools and visualizations that attempt to show the inner workings of neural networks, especially for educational purposes. One of the more notable examples is an open-source project by [Marijn van Vliet](https://github.com/wmvanvliet/scns/tree/main/visualizations/cnn), which uses Mayavi to render 3D visualizations of a neural network’s activation patterns. This program reads pre-recorded activity from a `.npz` file that was captured during the model's training process, displaying neuron activations across layers with animated transitions and even rotating views. It’s a solid step toward visualizing complex neural processes, but it’s fundamentally limited by the fact that everything is pre-rendered. The network isn’t *thinking* in real time in response to user interaction; it’s replaying captured data from training or inference sessions.

```py
@mlab.animate(delay=83, ui=True)
def anim():
    for frame in tqdm(list(range(1600))):
        if frame % 16 == 0:
            i = frame // 16
            img_input.mlab_source.scalars = activity['input'][i][0]
            for img, a in zip(img_conv1, activity['conv1'][i]):
                img.mlab_source.scalars = a
            for img, a in zip(img_conv2, activity['conv2'][i]):
                img.mlab_source.scalars = a
            act_fc1 = activity['fc1'][i]
            act_out = activity['output'][i]
            s = np.hstack((
                act_conv2.ravel() / act_conv2.max(),
                act_fc1 / act_fc1.max(),
                1 - (act_out / act_out.max())
            ))
            acts.mlab_source.scalars = s[len(act_conv2.ravel()):]
            connections.mlab_source.scalars = s
        mlab.view(azimuth=(frame / 2) % 360, elevation=80, distance=300, focalpoint=[0, 100, 0], reset_roll=False)
        mlab.savefig(f'/l/vanvlm1/scns/frame{frame:04d}.png')
        yield

anim()
```

That’s where TARS is fundamentally different.

TARS is built to be *live*. When a user interacts with the AI,they immediately see the neural network respond. Neurons light up based on actual inference occurring in the neural network, not on some pre-generated playback. This is done with a custom-built piece of software called a "Harness", which hooks into the neural network itself to capture neural activity in live-time, and stream it asynchronously through a secure pipeline.
```py
class Harness:
    def __init__(self, websocket: WebSocket = None):
         if websocket:
            import asyncio
        # Dictionary to store activations
        self.activations = {}
        self.input = None
        self.websocket = websocket

    def get_activation(self, name):
        """
        Hook function to capture the neural activity of a layer.
        """
        def hook(model, input, output):
            activation = output.detach().cpu().numpy()
            self.activations[name] = activation
            # Stream activation data if WebSocket is connected
            if self.websocket:
                # Send the data asynchronously outside the hook
                asyncio.create_task(self.websocket.send_json({
                    "layer": name,
                    "activation_shape": activation.shape,
                    "activation_data": activation.tolist()  # Convert to list for JSON serialization
                }))
        return hook
```
This neural activity can then be processed by a reciever, like the mobile app, and be rendered in live-time.
The experience is tailored around making machine learning tangible, with a tactile sense of cause and effect.

In addition, TARS introduces interactive nodes and synapses. Users can tap on individual neurons or synapses to see what they’re doing, or even view summaries of decision logic. That last feature is what really sets TARS apart: not only does the app show what the network is doing, it allows the neural network to *respond* in natural language.

Most competing solutions, whether academic demos or GitHub repositories, focus on static, often linear playback from data captured during an automated training session. TARS is different because it transforms the experience from passive observation into real-time interaction. Instead of watching a neural network from a distance, users step inside one. It's the difference between watching a simulation and playing a game.

## Conclusion

TARS represents a new kind of educational AI tool, one that goes beyond graphs and static models to deliver a truly immersive experience. By turning the neural network into something users can interact with, observe in real time, and learn from conversationally, the TARS mobile app has the potential to redefine how machine learning is taught and understood. This assignment lays the groundwork for the full design exploration to follow.