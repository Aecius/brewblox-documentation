# Categories and Other bits

## Seed Articles (Stuff that's slightly more basic than our target market but gets people interested in our knowledge)?

## Installation and Assembly Guides

### Fridge Hacking

Heating stuff:

- Hairdryers are overpowered for heating fridges. - This leads to a lack of precision.
- Heating options around 100W are recommended
  - Tubular Heaters can be great.
  - The Spark can also control heating belts.

### Sensors

    #### What sensor is right for me?
        - If you have a thermowell - simple sensor
        - If you have a mounting opening without a thermowell - a sensor of the appropriate mouning type
        - If you want to make an opening and lack a thermowell - Wall mounted sensors.
    #### One-Wire
    #### Thermowell
    #### Threaded
        ##### NPT-Threaded sensor in BSP threaded slot

### PWM Pump

- Type of control: Pulse Width Modulation
- Frequency: 100-1000Hz.
- Voltage of Blue PWM wire 5V

### Spark

    #### Software
        Installation instructions at: [https://brewblox.netlify.com/user/startup.html#what-you-will-need](https://brewblox.netlify.com/user/startup.html#what-you-will-need) .

        - What is required (and why)
            - A raspberry Pi
                - The Spark serves as a temperature controller, but it needs a server to render the UI and log data to.
                - The Raspberry Pi is a cheap and widely available linux capable computer with enough power to serve as a server, but still small enough to be a good always-on solution.
    #### Hardware
        ##### Connectors:
            The connectors are self-cutting. You just insert the wires without stripping and then push in the orange bits. Two teeth will cut through the insulation and make contact with the copper.

### SSR

    SSRs switch on an AC zero crossing, which will cause less interference due to inrush currents.For your heater, you should definitely pick an SSR, because by default uses PWM with a period of 4 seconds. Switching a mechanical relay every 4 seconds is not recommended. It is possible to change this period, but just using an SSR is better.The outputs of the spark are a digital 5V signal of max 20 mA. Probably not good enough to drive a relay coil directly.

### Heat Sinks

    - Does it need thermal paste?
        - In most case thermal paste is unecessary. But in those cases it does, the type that is used for PC processors works fine.

### Heating Elements

    #### What Heating Element is righ for me?
            - How much power do I need?
                - The formula for determining how quickly your element will heat: **
                    - > Volume in liters * 4200 / power of element in watts = seconds per degree Celsius
                    - Converted to american units: (Need to double check this)
                        - (Volume in gallons* 15849.05/ power of element in watts)/(9/5)= seconds per degree Fahrenheit
                - As a rule of thumb you will want the highest amount of power for your element *that power system can handle* - ~~you can always use an element as a lower power one, but the reverse isn't true~~. - You can always set it on a lower setting when you need less.
                    - How to determine the level of power your system can handle:
                        -
            - What shape is best for me?
                - Round elements:
                    - Round elements work great for most kettles:
                        - They disperse the heat more evenly throughout the kettle.
                        - > Our new round elements have a larger surface area than the straight elements. This means they have a lower watt density (power per square centimeter) for the same amount of power. Because of this they will scorch less and will be easier to clean.
                        - > Their round shape also helps to create a better whirlpool.
                - Straight elements:
                    - Traditional:
                    - Triclamp:
                        - If your kettle comes with a triclamp flange <port?> our straight tri-clamp heating elements might be a good choice.
                            - Like all triclamp systems they are easy to install and remove.
            - 1 or 3 phases?
                - What's the difference?
                    - >>> For 3-phase elements, the current is divided over 3 phases. This means that they require less current (per phase) than single phase elements. But if you have a very high current single-phase outlet, you can still use our round elements by connecting all 3 loops to this single phase.

                - What to use?

                    > Yes, the elements are basically 3 single-phase elements in one flange. You can connect them in any way you like.
                    Putting 2 or 3 in parallel on a single phase is possible. For a 3-phase connection, you would connect them in a star configuration.
                    Each element should get 230V RMS, but how you arrange them to achieve that is up to you.
                    With our BrewBlox software, we also support running multiple elements on a single fuse by quickly alternating them and balancing the time allocated to each element.
                    So you can run them at 40% at 60% at the same time for example.

                - Delta or Star?
            - What else do we need?
            - What size?
                - Round:
                    - The optimal size is about 10cm smaller in diameter than your kettle.


    #### How to Install
        https://www.notion.so/brewblox/How-to-Install-4af3119dd3ca4ef997ea63a3cd7a8445
    #### Maintenance
        > It is a bit hard to find what active ingredients VWP has, but what I can find suggests that VWP has chlorine in it.Chlorine causes pitting corrosion in stainless steel and should be avoided!Please see this topic:

        > [https://www.thehomebrewforum.co.uk/threads/using-vwp-cleaner.57664/](https://www.thehomebrewforum.co.uk/threads/using-vwp-cleaner.57664/)

        > Probably the VWP has already caused pitting, ruining the passivation and smoothness of the element.I would try to polish it and then passivate it again with an acid bath, followed by air drying.An oxi cleaner like PBW is a better choice.

### Stainless Steel Parts

    https://www.notion.so/brewblox/Stainless-Steel-Parts-028687fe4761457f97521f0227a9241e

## FAQs and Important Information

    - PWM pump Problems
    - Volume per kettel
    - Why we don't ship to Russia
    - The Basics of Electronics

## Manuals
