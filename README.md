# Лабораторная работа 0 
## Умножение матриц на GPU с CUDA 
**Язык программирования**: Python, v = 3.x.x\
**IDE**: google colab

### Информация о видеокарте
![GPU INFO](gpuinfo.png?raw=true)


### Таблица со всеми вычислениями
|size_of_matrix|time_for_CPU          |time_for_GPU_cupy     |time_for_GPU_pycuda   |time_for_GPU_skcuda   |boost cupy & cpu   |boost pycuda & cpu|boost skcuda & cpu |
|--------------|----------------------|----------------------|----------------------|----------------------|-------------------|------------------|-------------------|
|50            |0.00015735626220703125|0.0010256767272949219 |0.0001316070556640625 |0.00042939186096191406|0.15341701534170155|1.1956521739130435|0.36646307606885065|
|100           |0.004446744918823242  |9.655952453613281e-05 |8.344650268554688e-05 |0.00032448768615722656|46.05185185185185  |53.28857142857143 |13.703894195444526 |
|150           |0.0006020069122314453 |5.9604644775390625e-05|7.104873657226562e-05 |0.000217437744140625  |10.1               |8.473154362416107 |2.768640350877193  |
|200           |0.0008287429809570312 |5.6743621826171875e-05|8.559226989746094e-05 |0.0002243518829345703 |14.605042016806722 |9.682451253481894 |3.69394261424017   |
|250           |0.00145721435546875   |0.00012540817260742188|5.030632019042969e-05 |0.00022411346435546875|11.61977186311787  |28.966824644549764|6.502127659574468  |
|300           |0.0034193992614746094 |0.00015234947204589844|5.340576171875e-05    |0.00028967857360839844|22.444444444444443 |64.02678571428571 |11.804115226337448 |
|350           |0.0032570362091064453 |0.0002472400665283203 |5.841255187988281e-05 |0.00030231475830078125|13.17357762777242  |55.75918367346939 |10.773659305993691 |
|400           |0.002245187759399414  |5.698204040527344e-05 |4.6253204345703125e-05|0.0002739429473876953 |39.40167364016737  |48.54123711340206 |8.195822454308095  |
|450           |0.0032939910888671875 |5.650520324707031e-05 |4.601478576660156e-05 |0.0003619194030761719 |58.29535864978903  |71.58549222797927 |9.101449275362318  |
|500           |0.004160881042480469  |5.1975250244140625e-05|4.601478576660156e-05 |0.0006475448608398438 |80.05504587155963  |90.42487046632124 |6.425625920471282  |
|550           |0.005469322204589844  |7.009506225585938e-05 |4.9114227294921875e-05|0.0007307529449462891 |78.02721088435374  |111.35922330097087|7.484502446982056  |
|600           |0.009055614471435547  |6.508827209472656e-05 |4.3392181396484375e-05|0.0007197856903076172 |139.12820512820514 |208.69230769230768|12.58098708181517  |
|650           |0.008162975311279297  |6.29425048828125e-05  |4.935264587402344e-05 |0.0008013248443603516 |129.68939393939394 |165.40096618357487|10.186849152038084 |
|700           |0.01057744026184082   |7.319450378417969e-05 |5.1021575927734375e-05|0.0009527206420898438 |144.5114006514658  |207.31308411214954|11.102352352352352 |
|750           |0.013228893280029297  |5.054473876953125e-05 |4.6253204345703125e-05|0.0009698867797851562 |261.72641509433964 |286.0103092783505 |13.639626352015732 |
|800           |0.016279935836791992  |7.867813110351562e-05 |5.173683166503906e-05 |0.0010366439819335938 |206.9181818181818  |314.66820276497697|15.704461821527138 |
|850           |0.018755197525024414  |6.437301635742188e-05 |6.127357482910156e-05 |0.0011138916015625    |291.35185185185185 |306.08949416342415|16.83754280821918  |
|900           |0.022204875946044922  |6.508827209472656e-05 |5.0067901611328125e-05|0.0013191699981689453 |341.1501831501831  |443.4952380952381 |16.83245978673414  |
|950           |0.026683568954467773  |7.677078247070312e-05 |5.841255187988281e-05 |0.0013027191162109375 |347.5745341614907  |456.8122448979592 |20.482979502196194 |
|1000          |0.030781984329223633  |6.318092346191406e-05 |5.698204040527344e-05 |0.001497030258178711  |487.20377358490566 |540.2050209205021 |20.56203217072782  |
|1050          |0.03808116912841797   |5.626678466796875e-05 |5.030632019042969e-05 |0.001691579818725586  |676.7966101694915  |756.9857819905213 |22.51219168428471  |
|1100          |0.04244208335876465   |7.295608520507812e-05 |4.649162292480469e-05 |0.0018439292907714844 |581.7483660130719  |912.8974358974359 |23.01719679337988  |
|1150          |0.056807518005371094  |6.198883056640625e-05 |4.935264587402344e-05 |0.0018978118896484375 |916.4153846153846  |1151.0531400966183|29.93316582914573  |
|1200          |0.05380368232727051   |5.459785461425781e-05 |4.9591064453125e-05   |0.002110719680786133  |985.4541484716157  |1084.9471153846155|25.490681125042357 |
|1250          |0.06311631202697754   |5.626678466796875e-05 |5.3882598876953125e-05|0.0022513866424560547 |1121.7330508474577 |1171.367256637168 |28.03441702848671  |
|1300          |0.0819392204284668    |5.984306335449219e-05 |5.173683166503906e-05 |0.0026636123657226562 |1369.2350597609561 |1583.7695852534562|30.762441818832798 |
|1350          |0.08084344863891602   |5.7697296142578125e-05|5.245208740234375e-05 |0.003187417984008789  |1401.1652892561983 |1541.2818181818182|25.363303164036203 |
|1400          |0.08688068389892578   |6.341934204101562e-05 |5.269050598144531e-05 |0.002991914749145508  |1369.9398496240601 |1648.8868778280544|29.038489122639255 |
|1450          |0.09833002090454102   |7.271766662597656e-05 |9.465217590332031e-05 |0.003506183624267578  |1352.216393442623  |1038.8564231738035|28.044743642050864 |
|1500          |0.11658215522766113   |0.00011610984802246094|6.008148193359375e-05 |0.0036773681640625    |1004.0677618069815 |1940.4007936507937|31.70260632780083  |
|1550          |0.11305403709411621   |9.107589721679688e-05 |5.745887756347656e-05 |0.004410743713378906  |1241.3167539267015 |1967.5643153526971|25.631513513513514 |
|1600          |0.11394381523132324   |9.202957153320312e-05 |7.748603820800781e-05 |0.004045963287353516  |1238.1217616580311 |1470.5076923076922|28.16234531526223  |
|1650          |0.12989258766174316   |0.00011134147644042969|6.461143493652344e-05 |0.004346370697021484  |1166.6145610278372 |2010.3653136531366|29.885298957761933 |
|1700          |0.14515304565429688   |0.00010204315185546875|8.821487426757812e-05 |0.004801750183105469  |1422.4672897196263 |1645.4486486486487|30.2291956305859   |
|1750          |0.16179633140563965   |0.00011563301086425781|8.7738037109375e-05   |0.005202293395996094  |1399.2226804123711 |1844.0842391304348|31.10096241979835  |
|1800          |0.17334675788879395   |0.00010800361633300781|7.2479248046875e-05   |0.005623340606689453  |1605.008830022075  |2391.6743421052633|30.82629525989994  |
|1850          |0.19116497039794922   |0.0001049041748046875 |7.557868957519531e-05 |0.005824565887451172  |1822.2818181818182 |2529.3501577287066|32.82046663937781  |
|1900          |0.20978379249572754   |0.00010466575622558594|6.67572021484375e-05  |0.006070375442504883  |2004.3211845102505 |3142.489285714286 |34.55861906445151  |
|1950          |0.24511504173278809   |0.00010919570922851562|7.700920104980469e-05 |0.006924152374267578  |2244.731441048035  |3182.9318885448915|35.40000688657806  |

### Графики демонстрирующие скорость выполнения в зависимостии от размера матрицы, а так же прирост в скорости вычислений
![График демонстрирующий прирост в скорости вычислений](plot.svg?raw=true )
