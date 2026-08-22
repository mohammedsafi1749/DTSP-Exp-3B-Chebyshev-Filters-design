# EXP 3B: IIR-CHEBYSHEV-FITER-DESIGN

## AIM: 

 To design an IIR Chebyshev filter  using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (LPF): 
```
clc;
clear;
close;

// ============================================
// CHEBYSHEV TYPE-I IIR LOW-PASS FILTER
// ============================================

disp("========================================");
disp(" CHEBYSHEV TYPE-I IIR LOW-PASS FILTER");
disp("========================================");

// User input
Fs = input("Enter sampling frequency (Hz): ");
Fc = input("Enter cutoff frequency (Hz): ");
N  = input("Enter filter order: ");
Rp = input("Enter passband ripple (0 to 1): ");

// Validation
if Fs <= 0 then
    error("Sampling frequency must be positive.");
end

if Fc <= 0 | Fc >= Fs/2 then
    error("Cutoff frequency must be between 0 and Fs/2.");
end

if N <= 0 | N <> int(N) then
    error("Filter order must be a positive integer.");
end

if Rp <= 0 | Rp >= 1 then
    error("Ripple must be between 0 and 1.");
end

// Normalized cutoff frequency
Wc = Fc/Fs;

disp(" ");
disp("Normalized cutoff frequency:");
disp(Wc);

// Design Chebyshev Type-I Low-Pass Filter
hz = iir(N, "lp", "cheb1", Wc, [Rp 0]);

disp(" ");
disp("Filter Transfer Function:");
disp(hz);

// Frequency response
[hm, fr] = frmag(hz, 512);

// Convert frequency to Hz
f = fr * Fs;

// Plot
scf(1);
plot(f, hm);
xlabel("Frequency (Hz)");
ylabel("Magnitude");
title("Chebyshev Type-I IIR Low-Pass Filter");
xgrid();

```
## PROGRAM (HPF): 
```
clc;
clear;
close;

// ============================================
// CHEBYSHEV TYPE-I IIR HIGH-PASS FILTER
// ============================================

disp("========================================");
disp(" CHEBYSHEV TYPE-I IIR HIGH-PASS FILTER");
disp("========================================");

// User input
Fs = input("Enter sampling frequency (Hz): ");
Fc = input("Enter cutoff frequency (Hz): ");
N  = input("Enter filter order: ");
Rp = input("Enter passband ripple (0 to 1): ");

// Validation
if Fs <= 0 then
    error("Sampling frequency must be positive.");
end

if Fc <= 0 | Fc >= Fs/2 then
    error("Cutoff frequency must be between 0 and Fs/2.");
end

if N <= 0 | N <> int(N) then
    error("Filter order must be a positive integer.");
end

if Rp <= 0 | Rp >= 1 then
    error("Ripple must be between 0 and 1.");
end

// Normalized cutoff frequency
Wc = Fc/Fs;

disp(" ");
disp("Normalized cutoff frequency:");
disp(Wc);

// Design Chebyshev Type-I High-Pass Filter
hz = iir(N, "hp", "cheb1", Wc, [Rp 0]);

disp(" ");
disp("Filter Transfer Function:");
disp(hz);

// Frequency response
[hm, fr] = frmag(hz, 512);

// Convert frequency to Hz
f = fr * Fs;

// Plot
scf(1);
plot(f, hm);
xlabel("Frequency (Hz)");
ylabel("Magnitude");
title("Chebyshev Type-I IIR High-Pass Filter");
xgrid();

```
## PROGRAM (BPF):
```
clc;
clear;
close;

// ============================================
// CHEBYSHEV TYPE-I IIR BAND-PASS FILTER
// ============================================

disp("========================================");
disp(" CHEBYSHEV TYPE-I IIR BAND-PASS FILTER");
disp("========================================");

// User input
Fs = input("Enter sampling frequency (Hz): ");
F1 = input("Enter lower cutoff frequency (Hz): ");
F2 = input("Enter upper cutoff frequency (Hz): ");
N  = input("Enter filter order: ");
Rp = input("Enter passband ripple (0 to 1): ");

// Validation
if Fs <= 0 then
    error("Sampling frequency must be positive.");
end

if F1 <= 0 | F1 >= Fs/2 then
    error("Lower cutoff must be between 0 and Fs/2.");
end

if F2 <= 0 | F2 >= Fs/2 then
    error("Upper cutoff must be between 0 and Fs/2.");
end

if F1 >= F2 then
    error("Lower cutoff must be less than upper cutoff.");
end

if N <= 0 | N <> int(N) then
    error("Filter order must be a positive integer.");
end

if Rp <= 0 | Rp >= 1 then
    error("Ripple must be between 0 and 1.");
end

// Normalized cutoff frequencies
W1 = F1/Fs;
W2 = F2/Fs;

disp(" ");
disp("Lower normalized cutoff:");
disp(W1);

disp("Upper normalized cutoff:");
disp(W2);

// Design Chebyshev Type-I Band-Pass Filter
hz = iir(N, "bp", "cheb1", [W1 W2], [Rp 0]);

disp(" ");
disp("Filter Transfer Function:");
disp(hz);

// Frequency response
[hm, fr] = frmag(hz, 512);

// Convert frequency to Hz
f = fr * Fs;

// Plot
scf(1);
plot(f, hm);
xlabel("Frequency (Hz)");
ylabel("Magnitude");
title("Chebyshev Type-I IIR Band-Pass Filter");
xgrid();

```
## PROGRAM (BSF): 
```
clc;
clear;
close;

// ============================================
// CHEBYSHEV TYPE-I IIR BAND-STOP FILTER
// ============================================

disp("========================================");
disp(" CHEBYSHEV TYPE-I IIR BAND-STOP FILTER");
disp("========================================");

// User input
Fs = input("Enter sampling frequency (Hz): ");
F1 = input("Enter lower cutoff frequency (Hz): ");
F2 = input("Enter upper cutoff frequency (Hz): ");
N  = input("Enter filter order: ");
Rp = input("Enter passband ripple (0 to 1): ");

// Validation
if Fs <= 0 then
    error("Sampling frequency must be positive.");
end

if F1 <= 0 | F1 >= Fs/2 then
    error("Lower cutoff must be between 0 and Fs/2.");
end

if F2 <= 0 | F2 >= Fs/2 then
    error("Upper cutoff must be between 0 and Fs/2.");
end

if F1 >= F2 then
    error("Lower cutoff must be less than upper cutoff.");
end

if N <= 0 | N <> int(N) then
    error("Filter order must be a positive integer.");
end

if Rp <= 0 | Rp >= 1 then
    error("Ripple must be between 0 and 1.");
end

// Normalized cutoff frequencies
W1 = F1/Fs;
W2 = F2/Fs;

disp(" ");
disp("Lower normalized cutoff:");
disp(W1);

disp("Upper normalized cutoff:");
disp(W2);

// Design Chebyshev Type-I Band-Stop Filter
hz = iir(N, "sb", "cheb1", [W1 W2], [Rp 0]);

disp(" ");
disp("Filter Transfer Function:");
disp(hz);

// Frequency response
[hm, fr] = frmag(hz, 512);

// Convert frequency to Hz
f = fr * Fs;

// Plot
scf(1);
plot(f, hm);
xlabel("Frequency (Hz)");
ylabel("Magnitude");
title("Chebyshev Type-I IIR Band-Stop Filter");
xgrid();

```
## OUTPUT (LPF) : 


## OUTPUT (HPF) : 

## OUTPUT (BPF) : 


## OUTPUT (BSF) : 


## RESULT: 
