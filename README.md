![Docker's visualizer showing my two VM cluster running 5 flask instances](https://i.imgur.com/a/HEslKZ5)
Docker's visualizer showing my two VM cluster running 5 load-balanced flask instances.

# Building a Containerized Cluster
The goal was to become familiar with docker and its uses across multiple machines. I had initially planned on combinging Docker and Kubernetes for this (and still want to experiment with that), but it turns out Docker's swarm functionality was able to spin up exactly what I had in mind. I did this by following parts 1-5 of the Docker 'get-started' tutorial (https://docs.docker.com/get-started).

I also wanted to do this entirely within a tmux+vim environment so I spent a good amount of time configuring both to maximize productivity.

I did this project solo.

## Knowledge Acquired
First, I gained a familiarity with defining, building, publishing, and deploying a Docker image. I also became familiar with the basics of how a framework like Docker's swarm manages a cluster--assigning a manager and worker nodes. 

I also saw some serious productivity gains once I started leveraging [fzf](https://github.com/junegunn/fzf), an excellent fuzzy finder that makes finding and repeating lengthy commands in one's history very easy. 

Of course, the best way to really learn something is to break it and then be forced to fix it. In the process of editing the sample flask app that was run by my Docker image, I made some erroneous keystrokes in Vim and introduced a bug or two. I then went through the process of debugging a cluster with failing jobs, re-publishing the image, and then updating the cluster with the new image in place.

## What didn't work
I learned that tags are quite finicky in Docker. While they are technically mutable, meaning you can update an image tagged 'part2', they are canonically supposed to be immutable. As such, when I updated my image with the same tag, I had to force a re-pull on my cluster since it doesn't automatically recognize the fresher image. An annoying but effective way to learn best practices surrounding tagging images.

I also learned, painstakingly, that one hits Ctl-W-W to switch panes in Vim, and one hits Cmd-W to exit iTerm2. This caused me to have to rewrite this README. Not fun.

Docker's swarm functionality and higher-abstraction of a stack aren't exactly intuitive. I found the Docker container to be the most elegant part of this tech, but am still hoping that Kubernetes presents a more intuitive setup for cluster management.

