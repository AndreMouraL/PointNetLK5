# PointNetLK5: Point Cloud Registration using PointNet

# PointNetLK5: Uma extensão do PointNetLK: Registro de Nuvem de Pontos usando PointNet  

Código-Fonte Original:  
Yasuhiro Aoki  

Modificações e Extensão:  
André Moura  e Victor Coelho 

### Requerimentos:  
* PyTorch a versão mais recente e torchvision  
* NumPy  
* SciPy  
* MatPlotLib  
* ModelNet40l
* Python 3.x 
* Open3D
* Pandas

- **Ferramentas**:
  - Um ambiente compatível com GPU é recomendado para treinamento mais rápido.

---

### Principais arquivos para experimentos:  
* train_classifier.py: treina o classificador PointNet (usado para transferência de aprendizado)
Colab:!python train_classifier.py --dataset-path [Local do dataset ModelNet40l no seu Drive] --epochs 1 --outfile output_model --categoryfile [local: modelnet40l_half1.txt] --workers 1 (teste com 1 epoca).
* train_pointlk.py: treina o PointNet-LK  
Colab:!python train_pointlk.py --dataset-path  [Local do dataset ModelNet40l no seu Drive] --epochs 1 --outfile output_model --categoryfile  [local: modelnet40l_half1.txt] --workers 1
* generate_rotation.py: gera perturbações de 6 dimensões (rotação e translação) (para testes)  
Colab:!python pasta drive/PointNetLK5/experiments/generate_rotations.py \
-i [Local do dataset ModelNet40l no seu Driver] \
-o pasta drive/PointNetLK5/experiments/data/perturbations/output.csv \
--deg 45 --max-trans 0.1 --categoryfile [local: modelnet40l_half1.txt]

* test_pointlk.py: testa o PointNet-LK 
Colab:!python pasta drive/PointNetLK5/experiments/test_pointlk.py \
  --outfile output.csv \
  --dataset-path pasta [Local do dataset ModelNet40l no seu Drive] \
  --categoryfile pasta drive/PointNetLK5/experiments/sampledata/modelnet40l.txt \
  --perturbations pasta drive/PointNetLK5/experiments/data/perturbations.txt \
  --dataset-type modelnet \
  --format wv \
  --max-iter 20 \
  --dim-k 1024 \
  --symfn max \
  --delta 0.01 \
  --workers 4 \
  --device cpu
* test_icp.py: testa o ICP  
Colab: !python test_icp.py --outfile output.csv --dataset-path [Local do dataset ModelNet40l no seu Drive] --categoryfile pasta drive/PointNetLK5/experiments/data/categories.txt --perturbations pasta drive/PointNetLK5/experiments/data/perturbations.txt
* result_stat.py: calcula os erros médios dos testes acima 
Colab:  
!python result_stat.py --infile pasta drive/PointNetLK5/experiments/output.csv --hdr
### Extensão PointNetLK5  
Este projeto é uma extensão do PointNetLK, denominada PointNetLK5, desenvolvida por André Moura Lima e Victor Coelho da Silva.  
O objetivo do PointNetLK5 é expandir a funcionalidade do registro de nuvens de pontos com base em PointNet, introduzindo melhorias e novos recursos.  
O desenvolvimento e os experimentos foram realizados utilizando o Google Colab, facilitando a implementação e a visualização dos resultados como nosso dataset ModelNet40l, que é uma extensão ModelNet40.

# ModelNet40L Dataset (Criação de Andre Moura e Victor Coelho).

## Descrição Geral
O **ModelNet40L** é uma extensão do famoso conjunto de dados **ModelNet40**, criado para fornecer uma base mais diversificada e rica para treinamento e teste de modelos de registro de nuvens de pontos. Ele inclui objetos históricos e culturais, ampliando as possibilidades de aplicação em cenários desafiadores.

---

## Estrutura do Dataset
O dataset é organizado em categorias, cada uma contendo arquivos no formato **.off** (Object File Format), representando objetos 3D. Abaixo estão as categorias incluídas:
O dataset foi escutado no driver  pois  os experimentos foi feitos no ambiente colab com classes:
- airplane
- busto
- canhao
- guarana
- libertadores
- lion
- pessoa
- poste
- ribeirao
- trono
---

## Objetivo do Dataset
- Enriquecer a diversidade de objetos no treinamento de modelos como o **PointNetLK** e **PointNetLK5**.
- Avaliar a robustez e generalização de modelos em cenários mais complexos e variados.
- Facilitar aplicações que demandam precisão no registro 3D, como realidade aumentada, mapeamento 3D e robótica.

---

## Formato dos Dados
- **.off (Object File Format)**: Cada arquivo representa a geometria 3D de um objeto. Este formato é amplamente utilizado na representação de malhas geométricas.

---

## Uso do Dataset
1. **Treinamento e Teste**:
   - Utilize scripts de treinamento como `train_pointlk.py` para treinar modelos com os dados do ModelNet40L.
   - Teste modelos utilizando `test_pointlk.py` ou outros scripts fornecidos.

2. **Visualização**:
   - Use ferramentas como Open3D ou Matplotlib para visualizar os objetos e verificar os resultados.

3. **Geração de Perturbações**:
   - Aplique transformações (rotação e translação) com scripts como `generate_rotation.py` para testar robustez.

---

  
## Licença
O uso dataset  ModelNet40l é restrito a fins educacionais e de pesquisa. Para utilizações comerciais, entre em contato com os desenvolvedores.
Contato : am.lima@discente.ufma.br (Andre Moura) e victor.coelho@discente.ufma.br (Victor Coelho).  

### Citação PointNetLK
```
@InProceedings{yaoki2019pointnetlk,
       author = {Aoki, Yasuhiro and Goforth, Hunter and Arun Srivatsan, Rangaprasad and Lucey, Simon},
       title = {PointNetLK: Robust & Efficient Point Cloud Registration Using PointNet},
       booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
       month = {June},
       year = {2019}
}
```
### Citação do PointNetLK5  
```
@Misc{moura2025pointnetlk5,
    author = {Moura L, André e Coelho, Victor},
    title = {PointNetLK5: Advances in Robust & Efficient Point Cloud Registration Using PointNet},
    howpublished = {https://github.com/AndreMouraL/PointNetLK5}},
    month = {January},
    year = {2025},
    note = {Extension of PointNetLK with new features and improvements. Development and visualization performed using Google Colab. Based on the original work presented at CVPR 2019.}
}
```
}

