# ArtigosPCSS
A ideia é colocar os artigos e refências a serem analisados para tirar a conclusão dos métodos a serem usados para a implementação em um carro autônomo utilizando o LiDAR. Lembrando que qualquer problema com permissão é necessário apenas logar no portal CAFe da UFG e clicar novamente no link

## Artigos a serem analisados
* String de busca atual: _LiDAR AND ROS AND point clouds semantic segmentation AND autonomous driving_
* Datasets citados até o momento (possui informações de artigos que não estão listados): SemanticKITTI (6x), NuScenes (2x), KITTI dataset (3x), KITTI 3D object detection dataset (2x),  KITTI Velodyne object detection dataset (1x), Semantic3D (2x), SemanticPOSS (1x), SqueezeSeg (1x), S3DIS (1x), Cityscapes (1x), SYNTHIA (1x), Apollo Point Cloud (1x).
* Classes de interesse:
  - Veículo
  - Veículo pesado
  - Motocicleta
  - Bicicleta
  - Pessoa
  - Rua
  - Calçada
  - Poste
  - Parede
  - Prédio
  - Vegetação
* Códigos open source para análises futuras: https://github.com/TiagoCortinhal/SalsaNext -  https://gitlab.com/aksoyeren/salsanet - https://github.com/ywangeq/PointSeg - https://github.com/pyun-ram/PointSeg - https://github.com/lvpeiqing/RIU-Net
* Abreviações ou siglas importantes:
  - CNN: Redes Neurais Convolucionais.
  - U-Net: Tipo de CNN muito utilizada na área de segmentação de imagens biomédicas.
  - MLP: Multilayer Perceptron ou Rede Neural Totalmente Conectada
  - Voxel: Imagem de uma região tridimensional limitada por tamanhos especificados, nos quais possuem suas próprias coordenadas de pontos nodais em um sistema, suas próprias formas, seu próprio parâmetro de estado que indica que pertence a um objeto modelado e possui propriedades de regiões modeladas.
1. Cylindrical and Asymmetrical 3D Convolution Networks for LiDAR Segmentation (2020)
   + Link para o artigo: https://arxiv.org/pdf/2011.10033.pdf
   + É proposto um framework inspirado em U-Nets que faz partições cilíndricas e CNNs assimétricas 3D ao invés de 2D para lidar com a esparsidade e variação de densidade da nuvem de pontos em ambientes outdoor. O objetivo é impor a partição cilíndrica para gerar a distribuição de pontos mais balanceada e robusta. Basicamente a nuvem de pontos é enviada para uma MLP para pegar as features de pontos e depois tranferí-las com base na partição cilíndrica. Então, as CNNs assimétricas 3D são usadas para gerar os outputs de voxel. Por fim, um modulo de pontos é introduzido para refinar esses outputs.
   + Datasets utilizados: SemanticKITTI e NuScenes

2. SalsaNet: Fast Road and Vehicle Segmentation in LiDAR Point Clouds for Autonomous Driving (2019)
   + Link para o artigo: https://arxiv.org/pdf/1909.08291.pdf
   + É utilizado uma arquitetura encoder-decoder para segmentar semanticamente ruas (espaços livres para dirigir) e pontos de veículos em tempo real usando apenas data do 3D LiDAR. Um conjunto grande de nuvem de pontos do LiDAR é anotado a partir da transferência de labels entre diferentes modalidades de sensores (de imagens de câmera para o LiDAR, por exemplo). É estudado dois métodos de projeção de nuvem de pontos (Bird Eye’s View e Spherical-Front View) 2D para comparar seus efeitos no processo de segmentação semântica em termos de acurácia e velocidade. Por fim é feita uma minuciosa comparação quantitativa usando o SalsaNet no KITTI dataset com diferentes métodos de segmentação da época.
   + O source code do método é disponibilizado aqui: https://gitlab.com/aksoyeren/salsanet
   + Datasets utilizados: KITTI dataset, MultiNet (rede neural open source treinada no benchmark de detecção de ruas do KITTI)

3. PointSeg: Real-Time Semantic Segmentation Based on 3D LiDAR Point Cloud (2018)
   + Link para o artigo: https://arxiv.org/pdf/1807.06288.pdf
   + É proposto um método end-to-end de segmentação semântica baseado em imagens esféricas para objetos de rua. A imagem esférica é transformada a partir da nuvem de pontos do LiDAR com dimensões 64 x 512 x 5 e usada como input da CNN para prever a máscara semântica pontual. É usada a estrutura SqueezeNet para redes leves com o método SqueezeSeg, além de ideias de métodos como PSPNet que foram aplicados na CNN. O SqueezeSeg deve transformar a nuvem de pontos em uma imagem esférica e faz com que a CNN do PointSeg aceite a informação. Pode ser aplicada diretamente no sistema de direção autônoma com uma interface eficiente com uma curva de aprendizado simples e de fácil implementação.
   + Datasets utilizados: KITTI 3D object detection dataset e KITTI dataset

4. RIU-Net: Embarrassingly simple semantic segmentation of 3D LiDAR point cloud (2019)
   + Link para o artigo: https://arxiv.org/pdf/1905.08748.pdf
   + É proposto um método de adaptação muito simples de U-Nets para a segmentação de nuvens de pontos do LiDAR por meio de imagens de alcance 2D (Range-Image U-net). As imagens são tiradas da nuvem 3D do LiDAR explorando a topologia do sensor e focando em objetos como carros, pedestres e ciclistas, por exemplo. Para treinar o modelo, cada imagem de alcance é retirada do KITTI object detection dataset e é usada como input em uma CNN.
   + Datasets utilizados: KITTI 3D object detection dataset
     
5. SemanticKITTI: A Dataset for Semantic Scene Understanding of LiDAR Sequences (2019)
   + Link para o artigo: https://arxiv.org/pdf/1904.01416.pdf
   + Link para vídeo de apresentação do artigo na conferência ICCV: https://www.youtube.com/watch?v=3qNOXvkpK4I
   + Link para site do dataset: http://semantic-kitti.org/
   + __Leitura pendente__

6. MVLidarNet: Real-Time Multi-Class Scene Understanding for Autonomous Driving Using Multiple Views (2020)
   + Link para o artigo: https://browse.arxiv.org/pdf/2006.05518.pdf
   + Link para o vídeo de apresentação do artigo na conferência IROS: https://www.youtube.com/watch?v=2ck5_sToayc
   + __Leitura pendente__

7. Efficient and Robust LiDAR-Based End-to-End Navigation (2021)
   + Link para o artigo: https://browse.arxiv.org/pdf/2105.09932.pdf
   + Link para o vídeo de apresentação do artigo na conferência ICRA: https://www.youtube.com/watch?v=5ZyhHxjgUGo
   + __Leitura pendente__
  
8. Large-scale Point Cloud Semantic Segmentation with Superpoint Graphs (2022)
   + Link para o artigo: (https://openaccess.thecvf.com/content_cvpr_2018/papers/Landrieu_Large-Scale_Point_Cloud_CVPR_2018_paper.pdf)
   + É proposto um framework para segmentação semântica de nuvens de pontos 3D, que é capaz de segmentar objetos em subpartes geométricas simples e semânticas.  framework é baseado em uma abordagem de superpixels, que agrupa pontos em regiões homogêneas e compactas, e em uma rede neural convolucional que aprende a segmentação semântica desses superpixels.
   + Datasets utilizados: Semantic3D (https://www.semantic3d.net/) e S3DIS (https://paperswithcode.com/dataset/s3dis).

9. Real-Time LiDAR Point Cloud Semantic Segmentation for Autonomous Drivings (2019)
   + Link para o artigo: https://www.mdpi.com/2079-9292/11/1/11
   + __Pendente__
   + Datasets utilizados: Semantic-KITTI (http://www.semantic-kitti.org/).

10. Automated Evaluation of Semantic Segmentation Robustness for Autonomous Driving (2020)
    + Link para o artigo: https://ieeexplore-ieee-org.ez49.periodicos.capes.gov.br/document/8691698
    + __Pendente__
    + Datasets utilizados: Cityscapes (https://www.cityscapes-dataset.com/).

11. Fast and Lite Point Cloud Semantic Segmentation for Autonomous Driving Utilizing LiDAR Synthetic Training Data (2022)
    + Link para o artigo: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9801844
    + __Pendente__
    + Datasets utilizados: Semantic-KITTI (http://www.semantic-kitti.org/).
   
12. PCSCNet: Fast 3D semantic segmentation of LiDAR point cloud for autonomous car using point convolution and sparse convolution network (2023)
    + Link para o artigo: https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9801844
    + __Pendente__
    + Datasets utilizados: Semantic-KITTI (http://www.semantic-kitti.org/), NuScenes (https://www.nuscenes.org/).
   
13. Improved 3D Semantic Segmentation Model Based on RGB Image and LiDAR Point Cloud Fusion for Automantic Driving (2023)
    + Link para o artigo: https://link-springer-com.ez49.periodicos.capes.gov.br/article/10.1007/s12239-023-0065-y
    + __Pendente__
    + Datasets utilizados: Semantic-KITTI (http://www.semantic-kitti.org/).
   
14. Simulating LIDAR Point Cloud for Autonomous Driving using Real-world Scenes and Traffic Flows (2018)
    + Link para o artigo: https://www.researchgate.net/profile/Dingfu-Zhou/publication/329057353_Simulating_LIDAR_Point_Cloud_for_Autonomous_Driving_using_Real-world_Scenes_and_Traffic_Flows/links/5c22ea0f92851c22a3463a25/Simulating-LIDAR-Point-Cloud-for-Autonomous-Driving-using-Real-world-Scenes-and-Traffic-Flows.pdf
    + __Pendente__
    + Datasets utilizados: KITTI (https://www.cvlibs.net/datasets/kitti/), SYNTHIA (https://synthia-dataset.net/), Apollo Point Cloud (https://apolloscape.auto/).
## Categorização dos Datasets

1. NuScenes: A Multimodal dataset for Autonomous Driving (https://www.nuscenes.org/nuscenes)
   + Link para o artigo: https://arxiv.org/pdf/1903.11027.pdf
   + **Overview**: NuScenes é um dataset que carrega todo o conjunto de sensores de um carro autônomo: 6 câmeras, 5 radars e 1 lidar, todos com 360 graus de campo de visão. O dataset compreende 1000 cenas, cada uma de 20s de duração e _bounding boxes_ 3D totalmente anotadas para 23 classes e 8 atributos. Possui 7x mais anotações e 100x mais imagens que o KITTI dataset.
   + **Setup do carro**:![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/98bacc5b-85cf-458f-8d13-313b73661ca4)
   + **Sincronização de sensores**: A exposição da câmera é ativada quando o lidar no topo varre o centro do campo de visão da câmera. O _timestamp_ da imagem é o tempo da ativação da exposição, e o _timestamp_ do lidar é o tempo quando a rotação total do frame do lidar é concluída.
   + **Localização**: Devido a possíveis falhas de GPS em áreas urbanas densas, a localização do carro é feita a partir da criação de um mapa offline HD detalhado da nuvem de pontos do lidar. Enquanto as informações são coletadas, é utilizado o esquema de localização Monte Carlo
   + **Mapa**: É providenciado mapas semânticos fiéis das áreas relevantes. O mapa rasterizado original inclui apenas ruas e calçadas com uma resolução de 10px/m. O mapa vetorizado providencia informações de 11 classes semânticas. Por fim, é providenciado rotas básicas, nas quais são os caminhos ideias que um veículo autônomo deve seguir levando em consideração nenhum obstáculo com o objetivo de facilitar previsões de trajetória pelo fato de simplificar o espaço de procura por rotas viáveis. ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/28ae1706-27b0-4aab-b2b3-1839da7931bc)

   + **Seleção de cenas**: São 1000 cenas de 20s cada, incluindo trânsitos de alta densidade (interseções, obras, etc...), classes raras (ambulância, animais, etc...), situações de trânsito potencialmente perigosas (pedestres não atravessando na faixa, comportamentos de trânsitos incorretos, etc...), manobras (mudança de faixa, curvas, paradas) e outras situações que possam ser difíceis para um veículo autônomo.
   + **Anotação de Data**: É amostrado _keyframes_ (imagem, lidar, radar) a 2Hz. São anotadas todas as 23 classes de objetos em cada _keyframe_ com uma categoria semântica, atributos (visibilidade, atividade e pose) e um cubóide (_bounding box_) modelado como x, y, z, comprimento, altura e ângulo de guinada. A anotação é contínua perante cada cena se elas são cobertas por pelo menos 1 ponto da nuvem do lidar ou do radar com frequências de captura de 12Hz (câmera), 13Hz (lidar) e 20Hz (radar).
   + Tabela das classes de plano frontal:
   + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/9cac52ff-2044-4167-9ae6-c527e9faf8d5)
   + Tabela das classes de plano de fundo:
   + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/4ef033bb-af5a-4039-985b-28bd8922ef5e)
   + Tabela dos atributos:
   + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/c9fa576d-6d27-44cf-aee2-874a76db0364)
   + **Tasks e Métrica**:
       + Detecção: São detectados 10 classes de objeto com _bounding boxes_, atributos e velocidades. As 10 classes são um subconjunto de todas as 23 classes anotadas. É utilizado a métrica de Precisão Média (AP), mas define o _match_ limitando a distância do centro 2D _d_ no chão ao invés de intersecção sobre união (IOU). O cálculo do AP é a área normalizada embaixo da curva de recuperação de precisão para recuperação e precisão acima de 10%. Caso pontos estejam abaixo de 10%, são removidos para minimizar o impacto de ruído. Se nenhum ponto nessa área é usado, o AP para tal classe é 0. Por fim, é medido os limites de _match_ de D = {0.5,1,2,4} metros e o conjunto de classes C como visto na imagem abaixo:
       + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/0f3770a6-2863-4f58-8236-df37df35408b)
       + Monitoramento:  Multi Object Tracking Accuracy (MOTA) e Multi Object Tracking Precision (MOTP), alarmes falsos por frame, trajetórias mais monitoradas, trajetórias mais rejeitadas, falsos positivos, falsos negativos, mudanças de identidade e fragmentações de monitoramento.

   + **STATUS**: _Provavelmente rejeitado_. Por mais que as métricas e categorias sejam promissoras, o fato da interpretação do lidar ser a partir de _bounding boxes_ foge do método proposto para o nosso projeto.

2. SemanticKITTI:  A Dataset for Semantic Scene Understanding of LiDAR Sequences (http://semantic-kitti.org/index.html)
   + Link para o artigo: https://arxiv.org/pdf/1904.01416.pdf
   + **Overview**: É um dataset baseado no _KITTI Vision Benchmark_ que usa todas as sequências providenciadas pelo teste de odometria com campo de visão de 360 graus. Ao todo são 28 classes e 22 sequências, sendo as 00-10 usadas para treino com scans individuais e sequenciais para interpretações semânticas como segmentação semântica e completude semântica de cenas. Já as sequências de 11-21 são usadas como teste mostrando uma grande variedade de situações desafiadoras de trânsito e tipos de ambiente.
   + **Processo de rotulagem**: Múltiplos scans são impostos uns sobre ous outros para obter uma varredura mais consistente de cada um. Primeiro é registrado e feito um loop perto das sequências usando um systema de laser SLAM para providenciar informações do sistema de navegação inerte mais consistententes. Então, a sequência de nuvem de pontos é subdividida em tiras de 100m por 100m e, para cada tira, é carregado apenas scans que sobrepôem as tiras. Para garantir consistência de scans sobrepondo as tiras, é mostrado todos os pontos dentro de cada uma e uma pewuena fronteira sobrepondo tiras vizinhas, tornando possível rotular a partir da tira vizinha. No total são 518 tiras e cerca de 1700 horas de rotulagem para o dataset.
   + **Estatísticas do dataset**: A figura abaixo mostra as classes rotuladas pelo dataset. As categorias principais estão rotuladas no eixo x e a quantidade de pontos anotados são o eixo y. É evidente que haverá um certo desequilíbrio na contagem de classes uma vez que há classes mais comuns que outras dependendo do lugar a ser avaliado, levando a conclusão que a distribuição de classes deve ser um problema que uma abordagem deve masterizar.![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/4e697995-02cc-4cc1-b78a-1cdbb644c7c7)
   + **Tasks e métricas**:
     + _Exmperimentos de varredura única_: O objetivo é inferir o rótulo de cada ponto tridimensional. Portanto, o input de todos os métodos avaliados é uma lista de coordenadas dos pontos tridimensionais junto com suas remissões, como por exemplo a força do feixe de laser refletido que depende da propriedade da surperfície atingida. Cada método deve então ter como output o rótulo de cada ponto do scan, como por exemplo uma rotação completa do lidar. Para avaliar a performance de rotulação, é utilizado o Índice médio de Jaccard ou a média da Intersecção sobre União (mIOU) em todas as classes, dado por:
       + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/4d65bbd2-0327-4e1b-a55d-b25ff3827daa)
       + sendo TP_c, FP_c e FN_c correspondentes aos números de verdadeiros positivos, falsos positivos e falsos negativos previstos para a classe c, e C é o número de classes (não estão distinguindo objetos movendo de estáticos).
     + _Experimentos de varredura múltipla_: O objetivo é permitir os métodos de explorarem a informação de uma sequência de múltiplos scans passados para melhorar a segmentação do scan atual. Após isso, o objetivo é fazer com que os métodos consigam distinguir objetos e classes que estão movendo de objetos estáticos. A avaliação é feita da mesma forma, pelo mIOU do scan atual sem se importar com a quantidade de scans passados foram usados para computar o resultado.
   + **Estrutura de Pastas**:
       + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/796cc91d-3066-4009-8041-8c91b8602b9a)

       + _dataset_ é a pasta principal que contem o dataset inteiro.
       + _sequences_ é a subpasta que está dentro da pasta _dataset_ e contem as informações organizadas pelas sequências. Cada sequência representa uma situação contínua de direção.
       + _<sequence_number>_ é a subpasta que está dentro da pasta _sequences_ e representa o número da sequência específica (00,01,02,...,21).
       + _velodyne_ é a subpasta que está dentro da pasta _<sequence_number>_ que contem a informação da nuvem de pontos do LiDAR na forma de arquivos binários (.bin).
       + _labels_ é a subpasta que está dentro da pasta _<sequence_number>_ que contem a informação verdadeira rotulada em um _uint32_ para cara ponto correspondente do scan do Velodyne (.label), podendo ser informações sobre classes de objetos (carros, pedestres e superfícies).
       + _calib_ é a subpasta que está dentro da pasta _<sequence_number>_ que contem a informação de calibragem como setup do sensor, parâmetros intrínsicos e extrínsicos (.txt).
       + _poses_ é a subpasta que está dentro da pasta _<sequence_number>_ que contem a informação sobre poses do sensor em difenrentes tempos. Essencial para entender o arranjo espacial dos sensores durante a coleta de dados (.txt).
       + _timestamps_ é a subpasta que está dentro da pasta _<sequence_number>_ que armazena os _timestamps_ correspondentes de cada frame na sequência. Crucial para sincronizar dados de sensores diferentes (.txt). 

   + **STATUS**: _Selecionado para confirmação_. É o dataset pioneiro dos estudos sobre segmentação semântica e oferece as ferramentas na forma que precisamos com uma métrica básica para análise de dados.

3. Appolo Scapes: Open Dataset for Autonomous Driving and its Application (https://apolloscape.auto/)
   + Link para o artigo: https://arxiv.org/pdf/1803.06184.pdf
   + Links relevantes: https://github.com/ApolloScapeAuto/dataset-api, https://apolloscape.auto/tracking.html.
   + **Overview**: É um conjunto de dados extenso de LIDAR para condução autônoma. Ele contém 100.000 quadros de nuvem de pontos reais para treinamento e 20.000 para teste, incluindo trajetórias de 1000 km para o tráfego urbano. Esses dados reais foram rotulados para um campo de visão de 360 graus. Os obstáculos rotulados foram categorizados em quatro classes, incluindo aproximadamente 768.950 carros comuns, 103.092 veículos grandes (como caminhões e ônibus), 160.897 ciclistas, 160.897 pedestres, 160.897 cones de tráfego e 160.897 outros objetos desconhecidos. "O conjunto de dados de Análise de Cena" (Scene parsing) fornece 146.997 quadros com anotações correspondentes a nível de pixel e informações de pose, além de mapas de profundidade para o plano de fundo estático.
   + **Setup do carro**:<br>
   ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/a292f911-a526-4ea0-a9fd-7216b0383631)

   + **Sistema de coleta**: Usa o Riegl VMX-1HA (http://www.riegl.com/) como a plataforma de aquisição para coletar ambientes 3D estáticos, além de sistemas de câmeras e lasers posicionados como indica a figura:<br>
![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/62149165-b219-4ef4-9210-9eef0f2d0c4f)<br>
   o mesmo também contém um conjunto de sensores que inclui uma Unidade de Medição Inercial (IMU) e um Sistema Global de Navegação por Satélite (GNSS), que oferecem informações precisas de posição, inclinação (roll & pitch), e orientação (heading). Para obter informações de GPS/IMU altamente precisas, é estabelecida uma base temporária de GPS nas proximidades do local de coleta. Tudo isso é feito em um veículo operaando normalmente a uma velocidade de 30 km por hora, com as câmeras sendo acionadas a cada metro (30fps).
   + **Comparação com outros datasets**: Número total e médio de instâncias nos conjuntos de dados KITTI, Cityscapes, BDD100K, e ApolloScape (nível de instância). O "pixel" representa anotações 2D a nível de pixel e "box" representa anotações a nível de caixa delimitadora.<br>
  ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/e706b765-d2a2-4cdc-b3ea-d805b838c63a)
   + **Semantic lanemark segmentation**: No ApolloScape, são utilizadas 27 marcações de faixa diferentes para avaliação. Os rótulos são definidos com base em atributos das marcas de faixa, incluindo cor (por exemplo, branca e amarela) e tipo (por exemplo, contínua e tracejada). Especificamente, 165.949 imagens de 3 locais de estrada são rotuladas e disponibilizadas online, onde 33.760 imagens são retidas para teste. Em comparação com outros conjuntos de dados publicamente disponíveis, como o KITTI ou o da Tusimple, o ApolloScape é o primeiro conjunto de dados grande que contém uma rica rotulagem semântica para marcas de faixa, abrangendo diversas variações. <br>
![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/a4a01f58-7713-4cea-b85c-019cadc378c8)
   + **Processo de rotulagem**: Para tornar o processo de rotulagem de quadros de vídeo preciso e eficiente, é proposto um pipeline de rotulagem ativa que considera conjuntamente informações 2D e 3D, conforme mostrado na figura:<br>
  ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/890f083b-d4d9-41c5-be18-9c00735390c6) <br>
O pipeline consiste principalmente em duas etapas: rotulagem 3D e rotulagem 2D, para lidar com objetos/planos de fundo estáticos e objetos em movimento, respectivamente. A ideia básica do pipeline é transferir os resultados rotulados em 3D para imagens 2D por meio de projeção de câmera.<br>
__Remoção de objetos em movimento__: A rotulagem de plano de fundo estático e objetos em movimento são tratados separadamente.<br>
__Splatting e Projeção__: Para cada ponto no ambiente, é adotada a técnica de "point splatting", ampliando o ponto 3D para um quadrado onde o tamanho do quadrado é determinado por sua classe semântica.<br>
__Rotulagem 2D de objetos e planos de fundo__: Os resultados da segmentação são combinados com um mapa de rótulos renderizado a partir de nuvens de pontos semânticas 3D.<br>
__Rotulagem de segmentos de marcas de faixa na estrada__: Realiza um processo de rotulagem semelhante ao da rotulagem 3D do plano de fundo rígido, rotulando cada ponto 3D com as etiquetas predefinidas de marcas de faixa. <br>
__Controle da qualidade dos rótulos__:  Em todas as tarefas de rotulagem 2D/3D, como nuvem de pontos 3D, plano de fundo 2D, instância 2D e faixa de marcação 3D, são inclusos estágios de verificação para controlar a qualidade do rótulo. Para cada tarefa, existem instruções detalhadas para treinar os rotuladores, e um rotulador está apto a começar a rotular após passar por um questionário projetado.<br>
   + **Definições das classes**: Possui 25 rótulos diferentes distribuídos em cinco grupos. Cada pixel é atribuído dois IDs: class ID e train ID. O train ID é usado no treinamento e pode ser ajustado conforme necessário. O valor 255 indica rótulos ignorados que não são avaliados durante a fase de teste. O class ID é utilizado para representar o rótulo nas anotações de referência.<br>
   ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/fc483a72-2102-4010-b867-ea26ddfbddd6)

   + **Métricas**: Usa métricas semelhantes às definidos no KITTI. O objetivo na tarefa de detecção de objetos 3D é treinar detectores de objetos para as classes 'veículo', 'pedestre' e 'ciclista'. Os detectores de objetos devem fornecer a caixa delimitadora 3D (dimensões 3D e posição 3D) e a pontuação/confiança da detecção.<br>
   Seguindo o CLEARMOT, utiliza a acurácia de rastreamento de múltiplos objetos (MOTA) como critério de avaliação.<br>
   ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/4d6f5b1b-524c-4316-9cbf-0e54b964c6d2)<br>
   Onde M, F, MME e Np são, respectivamente, o número de perdas, de falsos positivos, de desajustes, e de objetos presentes para o tempo t.<br>
   Para o objeto i e a hipótese do rastreador j, utiliza a sobreposição de interseção sobre união (IoU) para definir.<br>
   ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/67e34e07-5853-4939-878e-a9feed4d3db9)<br>
   A pontuação final será a MOTA média para Carro (C), Pedestre (P), e Ciclista (B).



   + **STATUS**: _Selecionado para confirmação_. É um dataset muito completo com diversas imagens e ferramentas, o mesmo possui uma anotação semântica pixel a pixel dos dados registrados fornecida em 2D, que talvez não seja utilizada, mas também possui uma anotação semântica ponto a ponto em 3D para 28 classes, que pode ser do interesse do projeto.


## Ferramentas
   1. SemanticKITTI API:
      + Link do repositório: https://github.com/PRBonn/semantic-kitti-api
      + **Overview**: Um dos fundadores do SemanticKITTI desenvolveu um repositório com scripts em Python para facilitar a abertura, visualização, o processo e avaliação de resultados da nuvem de pontos e rótulos provenientes do semanticKITTI dataset. O repositório conta com um tutorial simples de utilização no terminal, bem como um Dockerfile caso seja requerido utilização de cum conteiner para rodar o dataset, como no caso do projeto atual. Os códigos não foram detalhadamente analisados mas é percebido que estão comentados e cabe ao teste para confirmação.
      + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/4aea31e3-8e15-422c-a9cc-34751932524e)
   2. SemanticKITTI Point Labeler:
      + Link do repositório: https://github.com/jbehley/point_labeler
      + **Overview**: Um dos fundadores do semanticKITTI desenvolveu uma ferramenta feita em openGL e C++ para rotular uma única nuvem de pontos ou uma sequência delas. Basicamente, dado as poses da nuvem de pontos do KITTI dataset, a ferramenta carrega blocos/tiras de nuvem de pontos sobrepostas e, por isso, múltiplas nuvens de pontos são rotuladas de uma vez em uma certa área. O repositório possui uma documentação da ferramenta concisa ([wiki](https://github.com/jbehley/point_labeler/wiki)) e apresenta os pacotes e dependencias para utilizar, como o catkin e glow, por exemplo.
      + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/899a061b-4c12-4d62-9297-77c008f068de)

   3. CloudCompare:
      + Link da plataforma: https://www.danielgm.net/cc/
      + **Overview**: É uma plataforma feita em C++ de pré-processamento, processamento e visualização de nuvem de pontos 3D com uma interface gráfica, ferramentas de segmentação, automatização de processos por scripts (não inclusos) para integrar em pipelines de processamentos de dados e uma documentação intuitiva para o uso. Além disso, possui recursos avançados para análise estatística, análise visual dos resultados e operações de pré-processamento, como filtragem e remoção de outliers, por exemplo, antes da aplicação de um algoritmo de segmentação. É possível utilizar a plataforma com dados do ROS e vice-versa
      + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/66d0fccf-09a4-4769-bf49-b1192f2f708d)

   4. Open3D
      + Link da plataforma: http://www.open3d.org/
      + **Overview**: É uma plataforma em python/C++ mais orientada ao processamento de dados 3D, como nuvem de pontos e malhas, sendo possível integrar em pipelines de processamento mais amplo para uma análise de videos. Por enquanto, um ponto positivo é que a plataforma é compatível com o Jupyter Notebook ou Google Colab, porém a análise da nuvem de pontos das cenas do dataset selecionado provavelmente terá que ser feita frame a frame. É possível utilizar a plataforma com dados do ROS e vice-versa.
      + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70708476/70a55c92-34ac-482e-b584-e6883fceb451)
     
   5. ApolloScapeAuto API:
      + Link do repositório: https://github.com/ApolloScapeAuto/dataset-api
      + **Overview**: O Apollo é uma arquitetura para o desenvolvimento, teste e implantação de Veículos Autônomos. O ApolloScape, é uma parte desse projeto, sendo um conjunto de dados e ferramentas orientados para pesquisa em todos os aspectos da direção autônoma, desde percepção, navegação e controle até simulação. O repositório inclui Predição de Trajetória, Detecção e Rastreamento de Objetos 3D por LIDAR, Análise de Cena, Segmentação de Pistas, Autolocalização, Instância de Carro 3D, Estéreo e Conjunto de Dados de Preenchimento, todas as ferramentas possuem breves explicações do seu funcionamento, formato do arquivo e dados e método de avaliação, além do download do dataset, porém não possuem tutoriais para o uso da ferramenta.
      + ![image](https://github.com/alunos-pfc/ArtigosPCSS/assets/70653905/06db0b2e-2706-4766-a10d-4f1ca9399c16)











