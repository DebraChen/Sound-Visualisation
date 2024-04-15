let mic, fft;

function setup() {
    createCanvas(window.innerWidth, window.innerHeight);
    mic = new p5.AudioIn();
    mic.start();
    fft = new p5.FFT(0.8, 1024);  // Using a smaller bin count for more detail
    fft.setInput(mic);
    colorMode(HSB, 255);  // Use HSB color mode for richer colors
}

function draw() {
    background('#F4FCFF');  // Light blue background

    let spectrum = fft.analyze();
    noStroke();

    for (let i = 0; i < spectrum.length; i++) {
        let amplitude = spectrum[i];
        let x = map(i, 0, spectrum.length, 0, width);
        let y = map(amplitude, 0, 256, height / 2, 0);  // Centralize the waveform
        fill(154, 255, 255);  // HSB equivalent of #38CE98
        rect(x, height / 2, width / spectrum.length, y - height / 2);  // Draw bars from the middle to the top
        rect(x, height / 2, width / spectrum.length, height / 2 - y);  // Draw bars from the middle to the bottom
    }
}

function mousePressed() {
    userStartAudio();  // Ensures audio starts on user interaction
}
