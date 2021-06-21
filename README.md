# PracaMoja
% Parametry wejściowe
% fl = F * k
% fw = a*(dL/L)+b*(dL/L)^2+C
% stuktura punktu (F, dL)

pdL1 = [0.001: 0.001 : 0.003]; % wydłużenia dla części liniowej
pdL2 = [0.004: 0.001: 0.006]; % wydłużenia dla części wykładniczej
pF1 = [510, 1580, 2530]; % wartości siły dla części liniowej 
pF2 = [3510, 3730, 3890]; % wartości siły dla części wykładniczej

pF = [100:1:pF2(1)];
pFf = [pF2(1):1:5000];
rF1 = polyfit(pF1, pdL1, 1);
rl = @(x) rF1(1) * x + rF1(2);
rF2 = polyfit(pF2, pdL2, 2);
rw = @(x) rF2(1) * x.^2 + rF2(2) * x + rF2(3);
plot(pF, rl(pF), 'o-r');
hold on;
plot(pFf, rw(pFf), 'o-b');
ylabel("Wydłużenie");
xlabel("Siła [F]");
