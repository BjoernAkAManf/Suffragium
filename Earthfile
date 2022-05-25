build-linux:
    FROM barichello/godot-ci:3.4.4

    WORKDIR game
    COPY ./game .

    RUN mkdir -p /builds && \
        godot -v --export "Linux" /builds/suffragium

    SAVE ARTIFACT /builds/*

build-html5:
    FROM barichello/godot-ci:3.4.4

    WORKDIR game
    COPY ./game .

    RUN mkdir -p /builds && \
        godot -v --export "HTML5" /builds/suffragium.html

    SAVE ARTIFACT /builds/*

build-windows:
    FROM barichello/godot-ci:3.4.4

    WORKDIR game
    COPY ./game .

    RUN mkdir -p /builds && \
        godot -v --export "Windows" /builds/suffragium.exe

    SAVE ARTIFACT /builds/*

build:
    FROM busybox

    WORKDIR builds
    COPY +build-windows/ windows
    COPY +build-linux/ linux
    COPY +build-html5/ html5

    SAVE ARTIFACT . AS LOCAL ./builds