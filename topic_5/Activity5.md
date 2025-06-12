# Activity 5  
**Chris King**  
Grand Canyon University  
SDD-630 Mobile Software Development  
Professor Estey  
June 11, 2025 

---

### Comparison Table of Development Tools
| Name             | Advantages                                                                | Disadvantages                                                     | Popularity             | Age        | Framework or Language | Why do people choose this solution?                            | Why do people avoid this?                           |
| ---------------- | ------------------------------------------------------------------------- | ----------------------------------------------------------------- | ---------------------- | ---------- | --------------------- | -------------------------------------------------------------- | --------------------------------------------------- |
| **Swift**        | Native iOS support, modern syntax, fast performance, strong Apple backing | Apple-only, steep learning curve for newcomers                    | High (US), Rising      | \~10 years | Language              | It’s Apple’s official language, ideal for iOS/macOS/watchOS     | Not cross-platform, only good for Apple ecosystems  |
| **Kotlin**       | Native Android, concise syntax, interoperable with Java                   | Android-first, smaller community than Java or JS                  | High, Stable           | \~13 years | Language              | Official Android language; cross-platform potential with KMP   | iOS support via Kotlin Multiplatform still maturing |
| **React Native** | Cross-platform, hot reloading, JavaScript-based                           | Native performance limitations, dependency on 3rd-party libraries | High, Slightly Falling | \~9 years  | Framework             | JS devs can build mobile apps fast across platforms            | Performance bottlenecks in high-demand apps         |
| **Flutter**      | Cross-platform, highly customizable UI, fast dev cycle                    | Large binary size, less native feel, Dart language is niche       | Rising Quickly         | \~6 years  | Framework             | Strong Google support, great for rapid UI-rich app development | Dart language not widely used outside Flutter       |
| **Xamarin**      | C#/.NET-based, cross-platform, shared codebase                            | UI not always native, slower updates, heavier runtime             | Declining              | \~13 years | Framework             | Reuse .NET codebase, strong Microsoft support                  | Poor iOS performance, niche use case                |
| **Objective-C**  | Legacy Apple apps, mature, low-level control                              | Verbose, outdated compared to Swift                               | Falling                | \~40 years | Language              | Existing legacy codebases in iOS/macOS                         | Harder to maintain, Swift is now preferred          |
| **Java**         | Massive ecosystem, Android native, well-documented                        | Verbose syntax, not modern compared to Kotlin                     | High, Stable           | \~29 years | Language              | Ubiquitous, widely taught and used in enterprise dev           | Less modern features than Kotlin or Swift           |


### Language / Framework Recommendation for TARS App


## Introduction

As the development of the TARS mobile app continues, the most effective mobile development language and framework must be chosen to support our long-term goals. While several tools offer cross-platform capabilities and broader market reach, this recommendation supports building the TARS app natively in **Swift** for iOS.

## Justification for Choosing Swift

Swift is Apple’s official programming language for developing applications across iOS, macOS, watchOS, and tvOS. It is modern, type-safe, and performance-optimized for Apple's tightly integrated ecosystem. Since our intended release is focused on delivering a premium, aesthetic experience for educators, students, and tech-savvy parents, primarily in the U.S., where iOS has a dominant market share, Swift becomes a strategic choice.

Swift also allows developers to tap directly into native APIs such as Core ML, Vision, and Metal, which are extremely valuable for machine learning and real-time graphics, two key pillars of the TARS app.

Most importantly, applications that are based on artificial intelligence and deep learning are naturally subject to security risks, due to the nature of data science involved with such apps. Developing TARS within an operating system that, to this day, maintains such high levels of security, makes a lot of the existing security risks so much easier to manage.

## Addressing Cross-Platform Alternatives

Cross-platform solutions like Flutter or React Native promise shared codebases and cost savings, but come with performance tradeoffs. The TARS app involves advanced animation and real-time neural visualization features. These demand high efficiency, seamless UI responsiveness, and a liquid-fluid user experience - traits that are harder to guarantee with cross-platform layers.

In addition, our app needs tight integration with system-level components (e.g., custom drawing canvas, possibly camera access in the future), which are significantly more stable and performant when implemented natively.

### Cost vs. Quality: Is Cross-Platform Worth It?

While cross-platform tools may reduce short-term development cost, they risk inflating long-term maintenance costs due to workarounds, plug-in limitations, and performance issues. For a premium AI learning app like TARS, compromising on user experience is not acceptable.

Moreover, most cross-platform tools are still evolving rapidly. What works today might break tomorrow without community support or official updates, introducing maintenance risk in a long-term educational product.

## Are Newer Tools Better?

In theory, newer frameworks like Flutter offer exciting features. But choosing tools based purely on novelty can be dangerous. Businesses must consider:

- **Longevity** – Will this tool be supported in 5 years?
- **Support** – Is it easy to find developers trained in this tool?
- **Security** – Are patches and CVEs addressed quickly?

Swift checks all of these boxes. It has become a core part of Apple’s long-term development ecosystem and receives regular, stable updates. The Swift developer community is active, well-documented, and growing, especially in academic and startup environments.

## Consideration of Business Investment

Although Swift requires an investment in learning if the developers lacks experience, it aligns with industry-standard iOS development. Most enterprises with iOS products either use Swift or plan to migrate legacy Objective-C codebases to Swift.

If the organization already has Java/Kotlin talent, targeting Android may be worth exploring later. But for now, with a focus on premium user experience and performance, iOS development in Swift makes the strongest business case.

## Conclusion

While Kotlin, React Native, and Flutter each offer compelling reasons to be considered, **Swift** stands out for the TARS app due to its security, performance, integration capabilities, and long-term viability. As a native iOS app, TARS will benefit from Apple’s ecosystem, tight hardware/software integration, and access to machine learning frameworks essential for our digit recognition and neural visualization features.

Swift is recommended as the primary language for mobile app development of the TARS project.



