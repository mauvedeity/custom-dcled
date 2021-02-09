# custom-dcled

So this repo is my updated repo for the C code to support the [Dream Cheeky Message Board](https://www.amazon.co.uk/Dream-Cheeky-818-Message-Board/dp/B001KU43WK). According to the Amazon web page, the device itself is currently discontinued, but there may still be some out there. I bought mine from Maplin, which to be fair, is also discontinued.

I got the software ages ago, not long after I found the original device in a bargain bin. I downloaded the original software, which is the bulk of this repo, and then set about using it. I've made a fair few changes to it. The original software (and this README) is available by downloading the "2.2 release" from this repo. The 2.3 version is down to me. There is another repo [here on GitHub](https://github.com/Conservatory/dcled) for this software, and I will try and work out how to contribute my changes back to the repo.

This probably shouldn't be considered a good example of anything, including participating in OSS projects, but it may be useful if you've got one of those Dream Cheeky boards hanging around and want to make use of it.

I would suggest reading the instructions - I didn't, and as a result I've had a bunch of problems. I'm still working on sorting all of them, but in the meantime, the software mostly works for me.

## Notes

I've got my board plugged in to a Raspberry Pi, running Raspbian. As with any Raspberry Pi-based item, you need to make sure the power supply is up to driving the Pi plus the display. I had a few issues running the Pi off a mobile phone charger before I caved and bought the proper PSU.

I need to fix the permission issues properly.

I'm stull not 100% sure that I like the custom font I created.

## Remaining Issues

I've had to set the combined binary to `setuid root`. This is probably a bad idea, but that's better than what I did before, which was fiddle the permissions directly on the `dev` entry. On looking again, there's a file called `40-dcled.rules`, which is supposed to configure the system so `root` permissions aren't needed. I did not do this, which is why the `setuid` fixes my issue, but also means that you get an error if you try to run two instances at the same time, such as scroll a message while also displaying a clock. I'm not sure how that's meant to work, but at the moment, it doesn't. 
