# supercollider-x
Experimenting with SuperCollider

# Installation on Ubuntu

After several false starts on Fedora, I did this on Ubuntu.

```bash
sudo apt-get install supercollider jack-tools meterbridge
```

## JACK

Make yourself a member of the 'audio' group.  This permits JACK to get realtime access in the
kernel.  You have to at least log out and log in again.  I just reboot.

```bash
sudo usermod -a -G audio nick
sudo reboot
```

Once you are back, start `qjackctl`, the GUI interface to JACK.  If you're not using the default
audio interface, click `settings` and, using the `Interface` dropdown selector, choose your
preferred audio interface.

Click "Start" in `qjackctl`.  It should show 'started' in yellow.  If not, run `qjackctl` from a
terminal window and look at any messages that appear.

## scide

### Using the interpreter interactively

The IDE may be started in a terminal or through Gnome.  It has three panels: a code editor on the
left, a help browser in the upper right and a "Post Messages" (console output) in the lower
right.

There is no REPL.  Instead, code is selected in the editor and executed with <Shift-return>. Here
is a slightly expanded 'Hello World' example to illustrate the very basics:

```text
(
 "Hello ".post;
 "World!".postln;
)
```

Execute this by clicking the '(' in the IDE editor.  The parenthesized text will be selected and
highlighted in yellow.  Press <Control-return>.  The code will be interpreted and the output
shown in the lower-right "POST message" window.

Statements are semicolon terminated.

### Producing a sound

Sound production requires:

1. Start the sound synthesizer service
1. Know how to stop all sound production
1. Instruct your IDE to tell the sound server to produce a sound.

`scsynth`, the sound server, can be started from the IDE with <Control-b> or with the menu selection
`Language :: Boot server`.

All sound production will stop when <Control-.> (<Control-period>) is pressed.

Place the cursor on the following line in the editor and press <Shift-return>

```text
{ [SinOsc.ar(440, 0, 0.2), SinOsc.ar(442, 0, 0.2)] }.play;
```

If all went well, at this point SuperCollider and dependencies are installed, configured and
sound can be produced and controlled.
