# [Deprecated] phisap - PHIgros Semi-Automatic Player
[No Longer Maintained] ✨ A Semi-Automatic Song Player for (Similar to) Phigros Rhythm Games ✨

The author will no longer maintain this project. Users in need of similar functionality are advised to look for alternatives or forks of this project that are still being updated.

To view the source code, please refer to other branches:
+ [Stable Version](https://github.com/kvarenzn/phisap/tree/stable)
+ [Development Version](https://github.com/kvarenzn/phisap/tree/dev)

## A Little Chat
Half a year ago, I impulsively decided to flash the ROM on my main device. Before flashing, I forgot to back up the data for Phigros and Phira. After flashing, I found it troublesome to reinstall and set up both apps, so I didn’t bother.

Since then, I’ve been busy with academic and work-related matters, leaving no time to maintain or update this project. Now that my workload has eased up, I thought of resolving some of the issues listed here and adding features I had planned earlier. However, I just couldn’t muster the interest to do so. I likely won’t be interested in the future either, but who knows?

Therefore, I’ve decided to abandon this project—it’s not good to keep users waiting indefinitely for updates. This project was officially archived on **March 7, 2024**.

**@364hao** has helped answer/resolve many issues raised by users while I was unavailable. I would like to express my gratitude for their assistance.

This project will remain open-source under the WTFPL license. If you wish to continue developing phisap, feel free to fork and maintain your own version.

### Some Extra Thoughts

The origin of this project was quite simple. I had been playing (got into it after seeing a WATER gameplay video on Bilibili—the music was amazing) for less than three months. One day, while playing, I saw a tip that sparked the idea of making it a reality. I spent about two weeks of my spare time creating a prototype—a small script without even a command-line interface. I was ecstatic when the experiment succeeded. The first song phisap successfully completed was **WATER** on HD difficulty. (By the way, after practicing for some time, I was able to manually clear WATER on HD. As for IN, maybe next life!)

Later, I searched on GitHub to see if there were similar projects and was surprised to find none—guess everyone’s moral compass is quite high (lol). So, I modified the project, added a simple interface, and open-sourced it on GitHub. The reason for open-sourcing was straightforward: interesting things should be shared (provided they’re legal).

As for my attitude toward rhythm game masters, I’m indifferent. (Why even coin a term? It’s just scripting!) Perhaps it’s because I don’t use social platforms other than WeChat (and even that’s because everything requires it nowadays). I use Bilibili to watch VTubers (yes, I watch "costumed people"). None of my friends play rhythm games, so I have no one to share gameplay with (not that I have the urge to share—enjoying it myself is enough). Maybe these social aspects will improve as I grow older, but for now, I remain "naïve and inexperienced."

Regarding why I added Arcaea support, it was because a friend in the neighboring dorm (the only person I know who plays rhythm games) saw me using phisap on Data and asked if it could support Arcaea. I didn’t know what Rhythm Source Points were at the time but figured the mechanics should be similar, so I decided to give it a try. By the way, extracting Arcaea charts is indeed more convenient than Phigros—you just unzip the files. After three days of effort, I managed to create a usable version. Since I couldn’t afford to buy song packs, I tested it on free songs and found it could achieve AP. So, I also open-sourced that on GitHub. I’m grateful to Arcaea for making me revisit linear algebra from two years ago while calculating snake touch points—and thankfully, I hadn’t forgotten it completely.

Afterward, phisap evolved in two directions: a more user-friendly interface and better planning algorithms. I wasn’t keen on the first because I’m lazy and thought it might raise the bar for users a little, keeping it niche. But even I got fed up with my own interface eventually, so I slapped together a Qt interface, making it somewhat more presentable. The second direction, improving algorithms, was something I always tried. I wanted to AP the April Fools’ chart. I experimented with various approaches, rewriting the code dozens of times, but none worked perfectly. In the end, I kept three versions of the algorithm—Conservative, Aggressive, and Extreme—each with its limitations.

I wanted to continue refining the algorithms, but debugging was a hassle. During this time, I wrote a chart visualization tool that supported chart previews, gameplay demonstrations, frame-by-frame jumping, pause, rewind, and playback speed control. However, my business laptop’s GPU and CPU couldn’t handle the load (the interface was written with pyglet, the backend using OpenGL). Debugging would freeze the system, and I didn’t have the time to optimize, so the project was shelved.

As for Phira support, I was working on the Extreme algorithm and wanted advanced test samples. Then I found Phira, which had plenty of samples (lol). Since the original program was open-source, I created a chart parser that translated charts into a structure phisap could recognize (turns out learning Rust years ago came in handy). After a few algorithm tweaks, I managed to AP **IDOL IN**—it was as exhilarating as my first AP of WATER HD.

I tried APing more charts, but a few remained impossible regardless of algorithm tweaks. I realized it was a fundamental flaw in the existing algorithms, requiring either major revisions or a complete rewrite. Due to time constraints, I left it as is.

Finally, as mentioned earlier, I flashed my device and haven’t touched the project since. Considering future time constraints, this is the end of the road for phisap.

I deeply appreciate everyone who supported this project. Until we meet again!
