# custom-dcled

So this repo is my updated repo for the C code to support the [Dream Cheeky Message Board](https://www.amazon.co.uk/Dream-Cheeky-818-Message-Board/dp/B001KU43WK). According to the Amazon web page, the device itself is currently discontinued, but there may still be some out there. I bought mine from Maplin, which to be fair, is also discontinued.

I got the software ages ago, not long after I found the original device in a bargain bin. I downloaded the original software, which is the bulk of this repo, and then set about using it. I've made a fair few changes to it. The original software (and this README) is available by downloading the "2.2 release" from this repo. The 2.4 version is down to me. There is another repo [here on GitHub](https://github.com/Conservatory/dcled) for this software, and I will try and work out how to contribute my changes back to the repo.

This probably shouldn't be considered a good example of anything, including participating in OSS projects, but it may be useful if you've got one of those Dream Cheeky boards hanging around and want to make use of it.

I would suggest reading the instructions - I didn't, and as a result I've had a bunch of problems. I'm still working on sorting all of them, but in the meantime, the software mostly works for me.

## Notes

I've got my board plugged in to a Raspberry Pi, running Raspbian. As with any Raspberry Pi-based item, you need to make sure the power supply is up to driving the Pi plus the display. I had a few issues running the Pi off a mobile phone charger before I caved and bought the proper PSU.

I need to fix the permission issues properly.

I'm stull not 100% sure that I like the custom font I created.

## Changes

**Bug**: The screen didn't clear properly - when the last character scrolled onto the screen, it didn't get scrolled off again. There was code to do this, so I just added a call to the correct function to scroll the screen contents off again.

**Feature**: I added a new preamble graphic which flashes the whole screen on/off five times.

**Feature**: The fonts are lovely, but they're all typographically correct, which means they render oddly on the screen. I added another font (`7seg`) with big squared-off numbers that I find easier to read without my glasses on! Clearly my prescription has shifted since I bought the screen because that wasn't a problem before! Note that this changes the order that the program enumerates the fonts, so if you're using the `-g` parameter, you might want to check that the output font is the one you expect. My replacement font still has the letters and numbers in, as it's based off the built-in font.

## Remaining Issues

I've had to set the combined binary to `setuid root`. This is probably a bad idea, but that's better than what I did before, which was fiddle the permissions directly on the `dev` entry. On looking again, there's a file called `40-dcled.rules`, which is supposed to configure the system so `root` permissions aren't needed. I did not do this, which is why the `setuid` fixes my issue, but also means that you get an error if you try to run two instances at the same time, such as scroll a message while also displaying a clock. I'm not sure how that's meant to work, but at the moment, it doesn't. 

We seem to have versions 2.2 and 2.4. I'm not sure how I created version 2.4, but that's what the `Makefile` says it is.

I need to document the process of creating a new font, and upload a template font file.
