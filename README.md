# Лабораторная работа 0 
## Умножение матриц на GPU с CUDA 
**Язык программирования**: Python, v = 3.x.x\
**IDE**: google colab

### Информация о процессоре 
Intel(R) Xeon(R) CPU @ 2.20GHz

### Информация о видеокарте
![GPU INFO](gpuinfo.png?raw=true)


### Таблица со всеми вычислениями
|size_of_matrix                                                |time_for_CPU       |time_for_GPU_cupy     |time_for_GPU_pycuda   |time_for_GPU_skcuda   |boost cupy & cpu  |boost pycuda & cpu|boost skcuda & cpu|
|--------------------------------------------------------------|-------------------|----------------------|----------------------|----------------------|------------------|------------------|------------------|
|50                                                            |0.0001742839813232422|0.0018649101257324219 |0.00016832351684570312|0.0006241798400878906 |0.0934543594988494|1.0354107648725213|0.2792207792207792|
|100                                                           |0.009443044662475586|5.698204040527344e-05 |9.012222290039062e-05 |0.0001933574676513672 |165.71966527196653|104.78042328042328|48.83723797780518 |
|150                                                           |0.0001659393310546875|3.8623809814453125e-05|7.987022399902344e-05 |0.0002651214599609375 |4.296296296296297 |2.0776119402985076|0.6258992805755396|
|200                                                           |0.00038909912109375|5.984306335449219e-05 |4.696846008300781e-05 |0.0002460479736328125 |6.50199203187251  |8.284263959390863 |1.5813953488372092|
|250                                                           |0.0007069110870361328|5.1975250244140625e-05|4.410743713378906e-05 |0.00018334388732910156|13.600917431192661|16.027027027027028|3.8556566970091026|
|300                                                           |0.0010745525360107422|6.079673767089844e-05 |4.863739013671875e-05 |0.0002560615539550781 |17.67450980392157 |22.09313725490196 |4.196461824953445 |
|350                                                           |0.0019228458404541016|0.0002567768096923828 |5.054473876953125e-05 |0.00028324127197265625|7.488393686165274 |38.04245283018868 |6.788720538720539 |
|400                                                           |0.0018188953399658203|5.53131103515625e-05  |4.267692565917969e-05 |0.0002396106719970703 |32.883620689655174|42.62011173184357 |7.591044776119403 |
|450                                                           |0.0027201175689697266|5.507469177246094e-05 |4.9591064453125e-05   |0.00032401084899902344|49.38961038961039 |54.85096153846154 |8.39514348785872  |
|500                                                           |0.003815889358520508|4.839897155761719e-05 |5.125999450683594e-05 |0.0006022453308105469 |78.8423645320197  |74.44186046511628 |6.336104513064133 |
|550                                                           |0.005584239959716797|7.081031799316406e-05 |4.673004150390625e-05 |0.0006773471832275391 |78.86195286195286 |119.5             |8.244280183034142 |
|600                                                           |0.006295919418334961|6.628036499023438e-05 |4.3392181396484375e-05|0.0006568431854248047 |94.98920863309353 |145.0934065934066 |9.585117967332124 |
|650                                                           |0.0069429874420166016|6.4849853515625e-05   |7.867813110351562e-05 |0.000720977783203125  |107.0625          |88.24545454545455 |9.629960317460318 |
|700                                                           |0.00956416130065918|6.29425048828125e-05  |4.839897155761719e-05 |0.0007457733154296875 |151.95075757575756|197.61083743842366|12.824488491048593|
|750                                                           |0.011501789093017578|5.1975250244140625e-05|4.482269287109375e-05 |0.0008637905120849609 |221.29357798165137|256.6063829787234 |13.31548440518907 |
|800                                                           |0.013453483581542969|6.556510925292969e-05 |4.38690185546875e-05  |0.0009889602661132812 |205.19272727272727|306.67391304347825|13.603664416586307|
|850                                                           |0.016572237014770508|6.461143493652344e-05 |5.984306335449219e-05 |0.0010640621185302734 |256.4907749077491 |276.9282868525896 |15.57450145641945 |
|900                                                           |0.030832767486572266|6.389617919921875e-05 |4.506111145019531e-05 |0.0011801719665527344 |482.54477611940297|684.2433862433862 |26.125656565656566|
|950                                                           |0.024797916412353516|7.891654968261719e-05 |4.553794860839844e-05 |0.0012099742889404297 |314.2296072507553 |544.5549738219895 |20.49458128078818 |
|1000                                                          |0.0273740291595459 |5.8650970458984375e-05|4.5299530029296875e-05|0.0013976097106933594 |466.7276422764228 |604.2894736842105 |19.586318662572502|
|1050                                                          |0.03392171859741211|5.888938903808594e-05 |4.553794860839844e-05 |0.0016222000122070312 |576.0242914979757 |744.9109947643979 |20.91093474426808 |
|1100                                                          |0.0399169921875    |5.936622619628906e-05 |4.38690185546875e-05  |0.0017483234405517578 |672.3855421686746 |909.9130434782609 |22.831583253784263|
|1150                                                          |0.05141258239746094|7.987022399902344e-05 |5.888938903808594e-05 |0.001837015151977539  |643.7014925373135 |873.0364372469636 |27.9870214146658  |
|1200                                                          |0.04818367958068848|6.0558319091796875e-05|6.175041198730469e-05 |0.001997232437133789  |795.6574803149606 |780.2972972972973 |24.125223827145756|
|1250                                                          |0.06012248992919922|6.151199340820312e-05 |5.221366882324219e-05 |0.0021784305572509766 |977.4108527131783 |1151.4703196347032|27.598993104957863|
|1300                                                          |0.06436848640441895|7.224082946777344e-05 |5.364418029785156e-05 |0.0025129318237304688 |891.026402640264  |1199.9155555555556|25.614895635673623|
|1350                                                          |0.074371337890625  |7.295608520507812e-05 |5.340576171875e-05    |0.0031974315643310547 |1019.3986928104575|1392.5714285714287|23.259712176571472|
|1400                                                          |0.0889136791229248 |7.62939453125e-05     |5.030632019042969e-05 |0.0029532909393310547 |1165.409375       |1767.4454976303318|30.106644062323404|
|1450                                                          |0.09305453300476074|9.083747863769531e-05 |5.054473876953125e-05 |0.0034935474395751953 |1024.4068241469815|1841.0330188679245|26.63611547123456 |
|1500                                                          |0.11243200302124023|9.059906005859375e-05 |5.364418029785156e-05 |0.0036172866821289062 |1240.9842105263158|2095.8844444444444|31.081861323490642|
|1550                                                          |0.10320019721984863|8.821487426757812e-05 |5.841255187988281e-05 |0.004346609115600586  |1169.872972972973 |1766.7469387755102|23.742691020788765|
|1600                                                          |0.10597753524780273|9.059906005859375e-05 |5.507469177246094e-05 |0.0039730072021484375 |1169.7421052631578|1924.2510822510822|26.674387902064332|
|1650                                                          |0.11513447761535645|0.00010561943054199219|5.6743621826171875e-05|0.004258155822753906  |1090.0880361173815|2029.0294117647059|27.03857782754759 |
|1700                                                          |0.1422431468963623 |9.393692016601562e-05 |5.6743621826171875e-05|0.004748106002807617  |1514.2411167512691|2506.768907563025 |29.957870951544063|
|1750                                                          |0.14757108688354492|0.00011682510375976562|5.7220458984375e-05   |0.00495147705078125   |1263.1795918367347|2578.991666666667 |29.803447611710325|
|1800                                                          |0.16335558891296387|0.00010156631469726562|5.936622619628906e-05 |0.0054798126220703125 |1608.3638497652582|2751.6586345381525|29.810433344935607|
|1850                                                          |0.17212462425231934|0.00010395050048828125|5.841255187988281e-05 |0.005728960037231445  |1655.8325688073394|2946.7061224489794|30.044654375962377|
|1900                                                          |0.19133496284484863|0.00013589859008789062|5.841255187988281e-05 |0.005975246429443359  |1407.9245614035087|3275.579591836735 |32.02126725720214 |
|1950                                                          |0.20875287055969238|0.00011658668518066406|6.556510925292969e-05 |0.0067899227142333984 |1790.5378323108384|3183.9018181818183|30.744513501176307|
|2000                                                          |0.2203068733215332 |0.00010895729064941406|6.222724914550781e-05 |0.0071756839752197266 |2021.9562363238513|3540.360153256705 |30.701863973153472|


### Графики демонстрирующие скорость выполнения в зависимостии от размера матрицы, а так же прирост в скорости вычислений
![График демонстрирующий прирост в скорости вычислений](plot.svg?raw=true )
