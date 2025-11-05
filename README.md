# Simple Neural Amp

![Neural Amp UI](docs/neural_amp.png)

This is a tiny neural amp of a Marshall JCM 800. I wanted to learn how to train a neural network amp from scratch and run it in a real‑time plugin using JUCE and RTNeural. Think of it as a "hello world" for real‑time neural network audio processing.

Most of the code is based on Matthew Yee‑King's book, "Build AI‑Enhanced Audio Plugins with C++" ([github.com/yeeking/ai-enhanced-audio-book](https://github.com/yeeking/ai-enhanced-audio-book)). Thanks a lot to Mat I swapped the audio dataset in `training/` with my own and tweaked `CMakeLists.txt` so it builds out of the box.

To train, run
```bash
python train.py
```

Training data lives in `training/audio/`:
- `input/`: clean DI guitar (or whatever source) — this is the model input.
- `target/`: processed/amped signal that you want the network to learn.

Swap in your own pairs with matching filenames (same length/sample rate). The trainer will load `input/<name>.wav` and `target/<name>.wav` together.

To build, run

```bash
# generate build system (pick your preferred generator)

# macOS + Xcode (IDE)
cmake -S neural-amp-plugin -B neural-amp-plugin/build -G Xcode

# macOS/Linux CLI (Ninja)
cmake -S neural-amp-plugin -B neural-amp-plugin/build -G Ninja

# macOS/Linux CLI (Makefiles)
cmake -S neural-amp-plugin -B neural-amp-plugin/build
```

### Acknowledgments

Huge thanks to [@yeeking](https://github.com/yeeking) for the book and example code in "Build AI‑Enhanced Audio Plugins with C++", which this project is based on.

