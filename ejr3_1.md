clear all, close all, clc

Ts=1e-6;
t=0:Ts:3e-4;
x=cos(2*pi*10000*t);
subplot(2,1,1)
plot(t,x)

n=0:1:length(t)-1;
subplot(2,1,2)
A=stem(n,x),set(A,'markersize',1);

y=fft(x);
w=n*2*pi/(length(n)-1);
figure(2)%densidad espectral de potencia , discreta
subplot(2,1,1)
plot(w,(abs(y.^2)/pi))
subplot(2,1,2)
plot(w,angle(y))

f=w/(2*pi*Ts);
figure(3)%densidad espectral de potencia, continua
subplot(2,1,1)
plot(f,abs(y).^2*Ts.^2)
subplot(2,1,2)
plot(f,angle(y)),title('fase')


