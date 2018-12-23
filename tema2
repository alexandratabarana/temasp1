clc
T=40; 
%se introduce perioada initiala T[sec] cu valoarea din cerinta 40 s;
f=1/T;
w=2*pi*f;
rez=.001;
t = 0:rez:5*T;

N=50;
duty=17/T*100; %durata este D=17;
s=(1+square(w*t,duty))/2;
%am adunat un 1 si am impartit la 2 pentru ca
%amplitudinea semnalului sa ia valori intre 0 si 1.
%iar duty calculeaza cat la suta inseamna 17.

for n = -N:N
    C(n+N+1) = 1/T * integral(@(t)((1+square(w*t,42.5))/2).*exp(-1j*n*w*t),0,T) ;
    %calculul propriu-zis al coeficientiilor cu formula analitica;
end
sr = 0;
for n = -N:N 
    sr = sr + C(n+N+1)*exp(1j*n*w*t) ;
end
% se va reprezenta, pe același grafic(figura 1), semnalul inițial și semnalul
%reconstruit
figure(1);
hold on
%reprezentarea semnalului reconstrui:
plot(t,real(sr),'-.r'); %plot(t,real(sr),'-.r',t,imag(sr),'-.r');
plot(t,s);%reprezentarea semnalului initial
xlabel('Timpul[s]');
ylabel('Semnal x(t) si semnalul recompus x"(t)');
title('Semnalul initial si semnalul recompus') %se va afisa imaginea semnalului
%initial si cel recompus astfel: x(t) este reprezentat de semnalul cu linie
%solida, iar x"(t) este reprezentat de semnalul cu linie punctata, ceea ce 
%este reconstructia folosind N coeficienti, unde N=50;
hold off
%se va reprezenta (figura 2) spectrul de amplitundini in cea de-a doua
%figura pentru semnalul x(t);
figure(2);
hold on
%reţine graficul curent şi adaugă în aceeaşi fereastră grafică
%următoarele reprezentări grafice
stem((-N:N)*w,2*abs(C));
%functia stem este utilizata pentru reprezentarea functilor sau a
%seturi de date cu valori discrete
xlabel('Pulsatia w[rad/s]');
ylabel('Amplitudinile Ak');
title('Spectrul de Amplitudini al lui x(t)');
hold off
%dezactivează comanda hold on,dacă se doreşte în continuare reprezentarea
%în ferestre grafice separate
%Analiza Fourier a semnalelor analogice si anume continue ne permite
%sa exprimam orice semnal ce indeplineste criteriul de suficienta Diriclet
%intr-o suma finita de semnale elementare ceea ce este util in
%analiza usoara a circuitelor in domeniul fazorial sau construirea unui
%semnal necunoscut pe baza spectrului sau de amplitudini si de faze ce pot
%fi aflate cu un analizator de spectru.
