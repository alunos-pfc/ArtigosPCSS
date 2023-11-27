# ArtigosPCSS
A ideia é colocar os artigos e refências a serem analisados para tirar a conclusão dos métodos a serem usados para a implementação em um carro autônomo utilizando o LiDAR. Lembrando que qualquer problema com permissão é necessário apenas logar no portal CAFe da UFG e clicar novamente no link

## Artigos a serem analisados
* String de busca atual: _LiDAR AND ROS AND point clouds semantic segmentation AND autonomous driving_
* Datasets citados até o momento (possui informações de artigos que não estão listados): SemanticKITTI (4x), NuScenes (1x), KITTI dataset (2x), KITTI 3D object detection dataset (2x),  KITTI Velodyne object detection dataset (1x), Semantic3D (2x), SemanticPOSS (1x), SqueezeSeg (1x), S3DIS (1x), Cityscapes (1x).
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
   + **STATUS**: _Selecionado para confirmação_. É o dataset pioneiro dos estudos sobre segmentação semântica e oferece as ferramentas na forma que precisamos com uma métrica básica para análise de dados.




