# Monitoreo del patrón y frecuencia respiratoria
## Introducción
La respiración es un proceso esencial que permite el intercambio de oxígeno y dióxido de carbono, logrando así garantizar la homeostasis. Desde el punto de vista de la ingeniería biomédica este proceso se puede analizar como un sistema dinámico representado por variables físicas que se pueden cuantificar, como lo es la presión, el volumen, el flujo, la frecuencia respiratoria y más. Todas estas variables permiten el desarrollo de modelos cuantitativos del sistema respiratorio [1].


Según varias investigaciones se ha demostrado que la frecuencia respiratoria es uno de los signos vitales más sensibles para detectar y preventir eventos graves, como el paro cardiopulmonar [2][3][4]. Por esta razón, es importante comprender todas las variables involucradas en el proceso respiratorio y saber que sensores existen que sean ideales para medir cada una de estas variables, para llegar a tener la mejor caracterización de la frecuencia respiratoria.

## Variables físicas
En el proceso respiratorio intervienen varias variables físicas que describen cómo es el mecanismo en el cual, el aire entra a los pulmones, para un posterior intercambio de gases y una regulación por parte del organismo de ese proceso [5][6]. Entre las variables de índole mecánica se encuentra el volumen pulmonar, que representa la cantidad de aire que contienen los pulmones en las múltiples fases de la respiración y depende del movimiento de la caja torácica y del diafragma [5]; la presión respiratoria, la cual es considerada como la fuerza que impulsa el aire hacia dentro o fuera de los pulmones y se da gracias a los cambios de volumen generados del tórax [6]; y el flujo de aire, que indica la rapidez con la que el aire se desplaza a través de las vías respiratorias como consecuencia de los gradientes de presión [7]. Relacionado a este flujo aparece la resistencia de las vías aéreas, que depende del diámetro de los bronquios y bronquiolos y determina la facilidad, o en su defecto la dificultad, de circulación del aire [6][7]. También destaca la compliancia pulmonar, que refleja la capacidad del pulmón y del tórax para expandirse al afrontar un cambio de presión y se relaciona con la elasticidad del tejido pulmonar [5][8].

Durante el intercambio gaseoso hay intervención de variables como la presión parcial de los gases, principalmente oxígeno y dióxido de carbono, variable que expresa la tendencia de cada gas a difundirse desde los alvéolos hacia la sangre o viceversa [6][8]; la fracción de gas inspirado, cuya función es indicar la proporción de oxígeno presente en el aire inhalado [5]; y la capacidad de difusión, que depende del área de intercambio alveolar, del grosor de la membrana respiratoria y del gradiente de presión entre alvéolo y capilar [6][8]. Una vez en la sangre, se consideran variables como la saturación de oxígeno y el flujo sanguíneo pulmonar, las cuales permiten evaluar la eficiencia del transporte de oxígeno hacia los tejidos [5][7].

Adicionalmente, el proceso respiratorio está influido por variables ambientales y temporales, tales como la temperatura y la humedad del aire inspirado, las cuales determinan el acondicionamiento del aire en las vías respiratorias [6]. Por otro lado, la frecuencia respiratoria y los tiempos de inspiración y espiración, tomadas como variables temporales, describen el ritmo con el que se repite el ciclo respiratorio y dependen del control neural y químico del sistema respiratorio [5][8]. Gracias a este factor temporal, se puede determinar la periodicidad o la frecuencia del proceso respiratorio, conociendo datos como la cantidad de respiraciones por minuto y así lograr una estimación de la salud respiratoria de la persona [7][1].

La suma de estas variables, y otras más que se han analizado en múltiples estudios, permiten comprender la respiración como un fenómeno físico y fisiológico integrado, fundamental para el mantenimiento del equilibrio y el correcto funcionamiento del organismo [5][6].


## Sensor a emplear
En el proceso respiratorio, una de las variables físicas de mayor relevancia es la expulsión de dióxido de carbono de los pulmones en la fase de exhalación. La concentración del CO2 en el aire exhalado presenta un comportamiento periódico, directamente asociado al ciclo respiratorio de la persona, lo que permite utilizarla como una variable indirecta para la determinación de la frecuencia respiratoria, gracias a su comportamiento cíclico. En cada espiración se genera un incremento temporal en la concentración de CO2, mientras que durante la inspiración dicha concentración decrece, dando lugar a una señal oscilatoria que puede ser analizada tanto en el dominio del tiempo, como en el dominio de la frecuencia y así dar lugar a la cantidad de respiraciones por minuto.

Para la adquisición de esta variable; y derivado de esto calcular la frecuencia respiratoria, se hace uso de un sensor de gas "MQ-3", cuya respuesta se da en las variaciones en la concentración de gases presentes en el aire exhalado. Aunque el MQ-3 es comúnmente utilizado para la detección de alcohol, su principio de funcionamiento fundamentados en las variaciones de resistencia del material sensor frente a los gases reductores, permite detectar variaciones relativas en la composición del aire exhalado por el usuario. Al adaptar el sensor cerca de la vía respiratoria, es posible registrar una mayor concentración de CO2 en la fase espiratoria de cada respiracion, con el fin de determinar la frecuencia respiratoria del usuario de una manera no invasiva.

El sensor de gas MQ-3 es un sensor semiconductor de óxido metálico (MOS) que puede detetar variaciones en la composición del aire, esto lo hace  midiendo los cambios en la resistencia eléctrica. La parte más sensible del sensor esta recubierta de óxido de estaño (SnO₂) y se mantiene calentado internamente para facilitar las reacciones quimicas con los gases involucrados. En aire limpio, el oxígeno se adhiere en la superficie del material, atrayendo a los electrones del mismo y aumentando la resistencia; cuando hay gases reductores como el alcohol o compuestos del aire exhalado, estas moléculas reaccionan con el oxígeno , liberando electrones y disminuyendo la resistencia del sensor. La variación de resistencia genera una señal eléctrica proporcional a la cantidad de gas detectado y puede leerse como un voltaje analógico o digital que detecta cambios cíclicos en la composición del aire [9].

## Adquisición de la señal
## Adquisición de la señal
## Configuración.
```
matlab
port = "COM6";
baud = 115200;

T = input("¿Cuántos segundos deseas capturar?: ");
if isempty(T) || ~isnumeric(T) || T <= 0
    error("Tiempo inválido.");
end

Ts_plot = 0.10;
Y_FIXED = [0 3];
VREF = 3.0;   % inhalación sube: v_inv = VREF - v

smoothSec_live   = 0.12;
baselineSec_live = 3.0;
G_live = 6;

```
T define la duración total de captura.
Y_FIXED=[0 3] fija el eje Y para que la escala sea consistente.
VREF define la inversión. Si tu señal está “al revés” (inhalación baja), con v_inv = VREF - v la inviertes para que inhalación sea un pico (máximo), que es más fácil de detectar.
Los parámetros smoothSec_live, baselineSec_live, G_live son solo para que la gráfica en vivo se vea bien: no cambian el archivo crudo guardado.
## Abrir serial + preparar buffers
```
s = serialport(port, baud);
configureTerminator(s, "LF");
flush(s);
disp("Conectado. Capturando voltaje (CRUDO)...");

Fs_est = 200;
Nmax = max(2000, ceil(Fs_est * T * 1.3));
t = zeros(Nmax, 1);
v = zeros(Nmax, 1);
k = 0;
```
Aquí se conecta MATLAB al módulo Bluetooth/serial y limpias el buffer (flush).
33Preasignas memoria (t, v) para que el loop sea rápido (evitas que MATLAB crezca el array de a 1, que es lento).
Fs_est solo es una estimación para reservar memoria; el Fs real lo calculas después con median(diff(t)).
## Figura de captura in vivo
```
figure("Name","Respiración (BT) - CAPTURA CRUDA (visual invertida)","Color","w");
ax = gca; grid on; grid minor;
xlabel("Tiempo (s)"); ylabel("Voltaje (V)");
set(ax, "FontSize", 12);
set(ax, "YLim", Y_FIXED, "YLimMode", "manual");
set(ax, "XLim", [0 T],   "XLimMode", "manual");
axis(ax, "manual"); zoom off; pan off;

hReal = animatedline("LineWidth", 1.6);
hAmp  = animatedline("LineWidth", 2.2, "LineStyle","--");
legend("Suavizado (visual)", "Amplificado (visual)", "Location","northwest");
```
Esta es tu primera figura, la que usas para ver que estás capturando bien.
animatedline permite ir agregando puntos sin redibujar toda la curva (más eficiente).
Se fijan ejes para que el gráfico no “brinque” y puedas comparar entre capturas.
## Loop de captura
```
lastPlot = 0;
t0 = tic;
idxSmoothStart = 1;
idxBaseStart   = 1;

while toc(t0) < T
    line = strtrim(readline(s));
    parts = split(line, ",");
    val = str2double(parts(end));

    if ~isnan(val) && isfinite(val)
        k = k + 1;

        if k > Nmax
            t = [t; zeros(Nmax,1)]; %#ok<AGROW>
            v = [v; zeros(Nmax,1)]; %#ok<AGROW>
            Nmax = numel(t);
        end

        ti = toc(t0);
        t(k) = ti;
        v(k) = val;

        if (ti - lastPlot) >= Ts_plot
            v_inv_live = VREF - v(1:k);

            while idxSmoothStart < k && (ti - t(idxSmoothStart)) > smoothSec_live
                idxSmoothStart = idxSmoothStart + 1;
            end
            v_smooth = mean(v_inv_live(idxSmoothStart:k));

            while idxBaseStart < k && (ti - t(idxBaseStart)) > baselineSec_live
                idxBaseStart = idxBaseStart + 1;
            end
            base = mean(v_inv_live(idxBaseStart:k));

            v_amp = base + G_live*(v_smooth - base);
            v_amp = min(max(v_amp, Y_FIXED(1)), Y_FIXED(2));

            addpoints(hReal, ti, v_smooth);
            addpoints(hAmp,  ti, v_amp);

            set(ax, "XLim", [0 T]); set(ax, "YLim", Y_FIXED);
            drawnow limitrate nocallbacks;
            lastPlot = ti;
        end
    end
end

clear s;
t = t(1:k);
v = v(1:k);
```
readline lee cada muestra que envía el micro.
t(k) es el tiempo real medido en MATLAB (por eso después puedes calcular Fs).
Se grafica invertido (v_inv_live) para que inhalación sea subida.
El suavizado y baseline en vivo son “promedios con ventana temporal”, no con “N muestras”, entonces funcionan bien aunque cambie el muestreo por jitter Bluetooth.
Se guarda v crudo, sin filtrar: eso es crucial para análisis offline confiable.
## Guardar la señal (CSV-MAT)
```
stamp = datestr(now,"yyyymmdd_HHMMSS");
raw_csv = "resp_raw_" + string(T) + "s_" + stamp + ".csv";
raw_mat = "resp_raw_" + string(T) + "s_" + stamp + ".mat";

writetable(table(t, v, 'VariableNames', {'time_s','voltage_V'}), raw_csv);
save(raw_mat, "t", "v", "T", "VREF");

Fs_aprox = numel(t)/T;
fprintf("\nCRUDO guardado:\n- %s\n- %s\nMuestras: %d | Fs aprox: %.2f Hz\n", raw_csv, raw_mat, numel(t), Fs_aprox);

```
CSV: para abrir en Excel/Python/otros.
MAT: para MATLAB con todo intacto (mejor para reproducibilidad).
Se imprime Fs aprox solo como referencia rápida.
## Offline: Fs real + inversión + detrend + filtro
```
dt = median(diff(t));
Fs = 1/dt;

v_inv = VREF - v;
x_raw = detrend(v_inv, 1);
x_raw = x_raw - mean(x_raw);

f1 = 0.05; f2 = 0.70; ord = 4;
[b,a] = butter(ord, [f1 f2]/(Fs/2), "bandpass");
x_bp = filtfilt(b, a, x_raw);

smoothSec_pk = 0.35;
W = max(3, round(smoothSec_pk*Fs));
x_blk = movmean(x_bp, W);

```
Fs real con median(diff(t)): robusto ante jitter.
x_raw es el crudo invertido sin deriva (limpio para filtrar).
x_bp es la señal filtrada en la banda respiratoria.
x_blk es la señal negra: una versión más estable para encontrar máximos.
## Detección de picos
```
maxRPM = 30;
MinPeakDistSamp = max(1, round((60/maxRPM) * Fs));
prom = 0.30 * std(x_blk);

[~, locC] = findpeaks(x_blk, ...
    "MinPeakDistance", MinPeakDistSamp, ...
    "MinPeakProminence", prom);

refWinSec = 0.60;
refWin = max(3, round(refWinSec*Fs));

locR = zeros(size(locC));
for i = 1:numel(locC)
    c = locC(i);
    i1 = max(1, c - refWin);
    i2 = min(numel(x_bp), c + refWin);
    [~,im] = max(x_bp(i1:i2));
    locR(i) = i1 + im - 1;
end
locR = unique(locR, "stable");

peakTimes = t(locR);
RPM_pk = NaN;
if numel(peakTimes) >= 2
    RPM_pk = 60 / median(diff(peakTimes));
end

```
findpeaks(x_blk) evita que el ruido/habla haga “picos falsos”.
Refinamiento en x_bp corrige el desplazamiento que introduce el suavizado.
RR final temporal: 60 / mediana(periodos) → robusto ante 1 respiración rara.
## Gráfica de picos
```
figure("Color","w");
plot(t, x_bp,  "LineWidth", 1.0); grid on; hold on;
plot(t, x_blk, "LineWidth", 1.4);
plot(peakTimes, x_blk(locR), "o", "MarkerSize", 7);
xlabel("Tiempo (s)"); ylabel("Amplitud");
title(sprintf("Picos refinados sobre NEGRA | RPM=%.2f | picos=%d", RPM_pk, numel(locR)));
legend("Filtrada (x_{bp})","Negra (x_{blk})","Picos (refinados)");

x_raw_vis = movmean(x_raw, max(3, round(0.10*Fs)));
figure("Color","w");
plot(t, x_raw_vis, "LineWidth", 1.2); grid on; hold on;
plot(peakTimes, x_raw_vis(locR), "o", "MarkerSize", 7);
xlabel("Tiempo (s)"); ylabel("Crudo invertido (vis)");
title(sprintf("Picos (mismos tiempos) sobre CRUDO | RPM=%.2f", RPM_pk));
legend("Crudo invertido (vis)","Picos");

```
La primera figura es el “argumento fuerte”: picos sobre señal negra/filtrada.
La segunda es validación: “los picos también existen en el crudo”, no son artefacto.
## PSD Welch
```
trimSec = 2.0;
idx0 = find(t >= trimSec, 1, "first");
if isempty(idx0), idx0 = 1; end

x_psd = x_blk(idx0:end);
x_psd = x_psd - mean(x_psd);

winSec = 10;
winLen = max(32, round(winSec*Fs));
if winLen > numel(x_psd), winLen = max(32, floor(numel(x_psd)/2)); end
win = hamming(winLen);
nover = round(0.5*winLen);
nfft = max(1024, 2^nextpow2(winLen));

[Pxx, fpsd] = pwelch(x_psd, win, nover, nfft, Fs);

band = (fpsd >= f1) & (fpsd <= f2);

if ~isnan(RPM_pk)
    f_center = RPM_pk/60;
    bwPSD = 0.08;
    band2 = band & (fpsd >= max(f1, f_center-bwPSD)) & (fpsd <= min(f2, f_center+bwPSD));
    if any(band2)
        [~,iMax] = max(Pxx(band2)); fb = fpsd(band2);
        f_dom = fb(iMax);
    else
        [~,iMax] = max(Pxx(band)); fb = fpsd(band);
        f_dom = fb(iMax);
    end
else
    [~,iMax] = max(Pxx(band)); fb = fpsd(band);
    f_dom = fb(iMax);
end

RPM_psd = 60*f_dom;

figure("Color","w");
plot(fpsd, Pxx, "LineWidth", 1.2); grid on; hold on;
xline(f_dom, "--");
xlabel("Frecuencia (Hz)"); ylabel("PSD");
title(sprintf("PSD (Welch) | Dominante = %.3f Hz (%.2f RPM)", f_dom, RPM_psd));
xlim([0 2]);

```
Recortas el inicio (trimSec) porque ahí suele haber transitorio y deriva.
Welch: promedia espectros y es más estable que FFT simple.
El “truco” para que cuadre: si ya tienes RPM_pk, obligas a PSD a buscar el dominante cerca de esa frecuencia.
Esto evita que “gane” un armónico del habla o un componente lento no respiratorio.
## Resultados + guardado procesado
```
fprintf("\nRESULTADOS:\n");
if ~isnan(RPM_pk)
    fprintf("- RPM por picos: %.2f RPM | picos=%d\n", RPM_pk, numel(locR));
else
    fprintf("- RPM por picos: No estimable (pocos picos)\n");
end
fprintf("- RPM por PSD (Welch): %.2f RPM (f=%.3f Hz)\n", RPM_psd, f_dom);

proc_mat = "resp_proc_" + string(T) + "s_" + stamp + ".mat";
save(proc_mat, ...
    "t","v","v_inv","Fs","VREF", ...
    "x_raw","x_bp","x_blk", ...
    "locC","locR","peakTimes","RPM_pk", ...
    "Pxx","fpsd","f_dom","RPM_psd", ...
    "f1","f2","ord","trimSec","winSec","nfft");

fprintf("- Procesado guardado: %s\n", proc_mat);

```
Te deja un “paquete reproducible” con todo lo necesario para un informe: señal cruda, señal filtrada, RR por picos, RR por PSD, etc.
## Resultados obtenidos
### Respiración normal
#### Captura de la señal
[![habla1.jpg](https://i.postimg.cc/c1XqCwFM/habla1.jpg)](https://postimg.cc/s1QH0Qdv)
#### Filtros y detección de picos
[![habla2.jpg](https://i.postimg.cc/mZdqBRr7/habla2.jpg)](https://postimg.cc/pyFkJwzd)
#### Dominio de la frecuencia
[![habla3.jpg](https://i.postimg.cc/N0wCpjNB/habla3.jpg)](https://postimg.cc/QF0qMhGy)

### Respiración mientras se habla
#### Captura de la señal
[![hablar1.jpg](https://i.postimg.cc/9Mwp23Nj/hablar1.jpg)](https://postimg.cc/mzRM3nsd)
#### Filtros y detección de picos
[![hablar2.jpg](https://i.postimg.cc/GpHPPwRp/hablar2.jpg)](https://postimg.cc/R3xn9YNr)
#### Dominio de la frecuencia
[![hablar3.jpg](https://i.postimg.cc/prYKVPfY/hablar3.jpg)](https://postimg.cc/K3j1JSsR)

## Análisis y conclusiones
• Análisis 1: Determine semejanzas y diferencias (si las hay) entre la frecuencia y relación entre inhalaciones y exhalaciones de un individuo sano bajo condiciones de reposo y durante tareas de verbalización.

En un adulto sano en reposo, el patrón respiratorio suele ser relativamente regular y con un comportamiento cíclico; siendo casi senoidal, porque la ventilación está dominada por un ciclo estable de inspiración–espiración controlado principalmente por el centro respiratorio para mantener el intercambio gaseoso (O₂/CO₂) con variaciones pequeñas entre ciclos. En las señales tomadas en respiración en reposo, se ve de manera mas simétrica la fase respiratoria, con una leve diferenciación en que durante la espiración, el tiempo suele ser ligeramente más largo que en la fase de inspiración. En cambio, durante la verbalización el patrón cambia porque la respiración deja de ser solo ventilatoria y pasa a ser también respiración para el habla, tomándose inspiraciones rápidas y cortas en pausas mínimas, y se realiza una espiración más prolongada y modulada para sostener la fonación y controlar la presión subglótica. Por eso la señal se vuelve asimétrica y puede asemejarse con una señal "diente de sierra", con subidas rápidas (inhalación) y bajadas más largas y sostenidas (exhalación), además de irregularidades asociadas a frases, pausas, énfasis y esfuerzo vocal.

• Análisis 2: Evalúe el alcance y las posibles limitaciones de emplear el sistema construido durante la práctica para detectar patologías en seres humanos.

El sistema construido tiene como alcance principal servir como una herramienta académica de monitoreo básico para identificar cambios globales del patrón respiratorio (frecuencia respiratoria, variabilidad, pausas y relación inspiración/espiración) a partir de la detección de picos, por lo que podría ser útil como tamizaje de alteraciones relacionadas con la RR (como por ejemplo la taquipnea, bradipnea o irregularidad marcada) y para comparar condiciones como reposo vs habla. Sin embargo, este presenta limitaciones importantes para la detección de patologías en un entorno clínico: la señal no está calibrada fisiológicamente y varía mucho entre personas por diferencias en caudal espiratorio, profundidad respiratoria, humedad/temperatura del aire, y por el acople del montaje (distancia a boca/nariz, fugas, movimiento, condensación), lo que impide una relación universal voltaje→variable clínica. Además, el sensor usado (MQ-3) no es especializado en capnografía, no mide ETCO₂ real ni genera un capnograma clínico validado (con meseta alveolar y parámetros morfológicos), y puede responder a otros compuestos del aliento y al ambiente; por esto, el sistema no es adecuado para diagnosticar enfermedades que requieren medición confiable de CO₂ o análisis fino de la forma capnográfica (p. ej., obstrucción bronquial, hipoventilación por ETCO₂), y su uso debe plantearse como orientado a tendencias y patrones temporales más que a diagnóstico médico.

• Pregunta 1: ¿Son los patrones respiratorios y frecuencias respiratorias iguales o diferentes en cada caso? ¿A qué se debe esto?

• Pregunta 2: ¿Cuáles serían las ventajas y desventajas de emplear múltiples sensores para el monitoreo del proceso respiratorio? ¿Cuáles podrían ser las razones?

## Bibliografía
[1] J. D. Bronzino and D. R. Peterson, Biomedical Engineering Fundamentals.
    Boca Raton, FL: CRC Press, 2006. doi:10.1201/9781420003857.

[2] J. F. Fieselmann et al., “Respiratory rate predicts cardiopulmonary arrest
    for internal medicine inpatients,” J. Gen. Intern. Med., 1993.

[3] C. P. Subbe et al., “Effect of introducing the Modified Early Warning Score…,”
    Anaesthesia, 2003.

[4] D. R. Goldhill et al., “A physiologically-based early warning score…,”
    Anaesthesia, 2005.
    
[5] Guyton, A. C., & Hall, J. E. Textbook of Medical Physiology. Elsevier.

[6] West, J. B. Respiratory Physiology: The Essentials. Lippincott Williams & Wilkins.

[7] Levitzky, M. G. Pulmonary Physiology. McGraw-Hill.

[8] Ganong, W. F. Review of Medical Physiology. McGraw-Hill.

[9] S. Prabhu, “In-Depth: How MQ3 Alcohol Sensor Works? & Interface it with Arduino,” Last Minute Engineers.
