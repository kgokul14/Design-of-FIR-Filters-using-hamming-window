# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
close;

M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = ');

alpha = (M - 1)/2; // Center value

// Ideal impulse response
for n = 1:M
    k = (n - 1) - alpha;
    
    if (k == 0) then
        hd(n) = Wc / %pi;
    else
        hd(n) = sin(Wc * k) / (k * %pi);
    end
end

// Hamming Window
for n = 1:M
    W(n) = 0.54 - 0.46 * cos((2 * %pi * (n - 1)) / (M - 1));
end

// Windowed FIR coefficients
h = hd .* W;
disp(h, 'Filter Coefficients are');

// Frequency response
[hzm, fr] = frmag(h, 256);

// Magnitude response
subplot(2,1,1);
plot(2*fr, hzm);
xlabel('Normalized Digital Frequency (×π rad/sample)');
ylabel('Magnitude');
title('FIR LPF using Hamming Window');

// dB response (avoid log(0))
hzm_dB = 20 * log10(hzm + 1e-6);

subplot(2,1,2);
plot(2*fr, hzm_dB);
xlabel('Normalized Digital Frequency (×π rad/sample)');
ylabel('Magnitude (dB)');
title('FIR LPF using Hamming Window (dB)');
```
# OUTPUT
<img width="1918" height="1131" alt="image" src="https://github.com/user-attachments/assets/7d23e6f9-4732-40eb-b0d7-90cc167fc89f" />


# RESULT
To generate design of low pass FIR digital filter using SCILAB completed sucessfully.
