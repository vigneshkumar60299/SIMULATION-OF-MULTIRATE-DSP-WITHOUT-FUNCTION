# EXP 6 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify multirate DSP without function using SCILAB.

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 

//  SPEECH RECOGNITION USING SCILAB
```

clc;
close;


disp("Choose input signal:");
disp("1. Sine wave");
disp("2. Cosine wave");
disp("3. Ramp signal");
choice = input("Enter choice (1/2/3): ");


n = 0:%pi/50:2*%pi;

select choice
case 1 then
    x = sin(%pi*n);
    title_str = "Sine Signal";
case 2 then
    x = cos(%pi*n);
    title_str = "Cosine Signal";
case 3 then
    x = n;  // ramp
    title_str = "Ramp Signal";
end

M = input('Enter the downsampling factor M: ');
L = input('Enter the upsampling factor L: ');

downsampling_x = x(1:M:length(x));


disp(x,'Input signal x(n)=');
disp(downsampling_x,'Downsampled Signal');

figure(1);
subplot(2,1,1)
plot2d3(1:length(x), x);
xtitle(title_str + " (Original)");

subplot(2,1,2)
plot2d3(1:length(downsampling_x), downsampling_x);
xtitle("Downsampled Signal (Factor M = " + string(M) + ")");


upsampling_x = zeros(1, L*length(x));
for i = 1:length(x)
    upsampling_x((i-1)*L + 1) = x(i);
end

upsampling_zoh = [];
for i = 1:length(x)
    upsampling_zoh = [upsampling_zoh, ones(1,L)*x(i)];
end

disp(upsampling_x,'Upsampled Signal (Zero Insertion)');
disp(upsampling_zoh,'Upsampled Signal (ZOH Method)');


figure(2);

subplot(3,1,1);
plot2d3(x);
xtitle(title_str + " (Original)");

subplot(3,1,2);
plot2d3(upsampling_x);
xtitle("Upsampled (Zero Insertion, L = " + string(L) + ")");

subplot(3,1,3);
plot2d3(upsampling_zoh);
xtitle("Upsampled (Zero Order Hold)");
```


## OUTPUT: 
<img width="1918" height="952" alt="Screenshot 2026-03-26 162152" src="https://github.com/user-attachments/assets/c15e4881-3355-459c-9edd-cb7892cf3296" />


<img width="1919" height="955" alt="Screenshot 2026-03-26 162205" src="https://github.com/user-attachments/assets/edb48a43-6cfb-4a2f-a783-7d500b564803" />


## RESULT: 
Thus the decimation process by a factor M and interpolation process by a factor L using 
SCILAB was implemented. 
