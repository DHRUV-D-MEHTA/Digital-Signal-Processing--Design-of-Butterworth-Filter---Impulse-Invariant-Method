# Digital-Signal-Processing--Design-of-Butterworth-Filter---Impulse-Invariant-Method
## AIM:
To design of 2nd order Low Pass Butterworth Filter using using Impulse Invariant Transformation 
## SOFTWARE REQUIRED: 
MAT LAB R2012
## ALGORITHM:
Step 1: Open MAT LAB. Write the program. 

Step 2: Read the values of Ap,As,Pass band frequency,Stop band frequency.

Step 3: Initialise some conditions find out the order (N) value.

Step 4: Find out the transfer function of the filter and magnitude of that filter. 

Step 5: Plot the magnitude spectrum with x-label and y-label with suitable title. 

Step 6: Terminate the program.

## PROGRAM:

clc;

clear all;

close all;


% INPUTS

Ap = input('Enter the value of Ap: ');

As = input('Enter the value of As: ');

wp = input('Enter the PB frequency: ');

ws = input('Enter the SB frequency: ');

T  = input('Enter the value of time: ');

% PREWARPING

omega_p = wp / T;

omega_s = ws / T;

% CONVERT TO dB

alpha_p = -20*log10(Ap);

alpha_s = -20*log10(As);

% ORDER AND CUTOFF

[N, wc] = buttord(omega_p, omega_s, alpha_p, alpha_s, 's');

% NORMALISED TF

[num, den] = butter(N, 1, 's');

disp('Normalised Transfer Function:');

hs = tf(num, den)

% UNNORMALISED TF

[num1, den1] = butter(N, wc, 's');

disp('Unnormalised Transfer Function:');

hs1 = tf(num1, den1)

% IMPULSE INVARIANT TRANSFORMATION

[numz, denz] = impinvar(num1, den1, 1/T);

hz = tf(numz, denz, T)

disp('Digital Transfer Function:');

% FREQUENCY RESPONSE

w = 0:pi/16:pi;

y = freqz(numz, denz, w);

% MAGNITUDE

y1 = abs(y);

plot(w, y1);

xlabel('Frequency');

ylabel('Magnitude');

title('Magnitude Response Butterworth LPF');

grid on;

## OUTPUT:

## RESULT:
![WhatsApp Image 2026-04-01 at 6 06 47 PM](https://github.com/user-attachments/assets/3dc34cea-d71c-45d2-9994-1436da45f567)
