
## Dev
```bash
docker run -it --rm -d -p 8080:80 --name web -v ~/Documents/Projects/opal_shelter/:/usr/share/nginx/html nginx
```

## Video Processing
```bash
ffmpeg -i 21-0210\ Shelter\ Construction.mp4 -vcodec libx264 -pix_fmt yuv420p -profile:v baseline -level 3 -an -vf "scale=-1:600" -preset veryslow -g 4 video.mp4
```


options
- just embed the video: boring and unsexy--with no fancy scroll-based animiations--but basically guaranteed to work
- embed the video and tie video progress to scroll position (as demonstrated here): if we can make this work, this is probably the best approach, IF I can figure out the video compression. as is, the animation is pretty jerky



possible improvements and next steps
- the biggest improvement would just be me figuring out video encoding so we can compress this down some to smooth the animation.
- it might help if we simplify some of the animation stages. for example, rather than animating the entrance of each wall separately (top-left, top-right, bottom-right, bottom-left) resulting in 4 phases, we could animate them in over 2 phases (first enter top-left and top-right at the same time, next bottom-left and bottom-right at the same time). mostly, this sequencing will probably depend on what the accompanying text looks like. if there's a lot of text to explain a specific phase of the construction, it makes sense that that phase's animation would take longer. but if the animation of a phase of construction runs longer than the text, that animation should probably be cut down some.
- also, it might be good to open the video on something other than an empty white screen. one possibility: simply open w/ the basement floor already visible. another possibility: open on the fully constructed house (either fully colored, or the black/white wireframe), then fade away to basement slab, basement walls, floor, etc. alternatively, if there's copy text visible when the page first loads, this might not be necessary. the goal is just to have something (either an image or text) to prompt the user to start scrolling enough to start seeing the animation.
