# ArtigosPCSS
A ideia é colocar os artigos e refências a serem analisados para tirar a conclusão dos métodos a serem usados para a implementação em um carro autônomo utilizando o LiDAR. Lembrando que qualquer problema com permissão é necessário apenas logar no portal CAFe da UFG e clicar novamente no link

## Artigos a serem analisados
* String de busca atual: _LiDAR AND ROS AND point clouds semantic segmentation AND autonomous driving_
* Datasets citados até o momento (possui informações de artigos que não estão listados): SemanticKITTI (2x), NuScenes (1x), KITTI dataset (2x), KITTI 3D object detection dataset (2x),  KITTI Velodyne object detection dataset (1x), Semantic3D (1x), SemanticPOSS (1x), SqueezeSeg (1x)
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
