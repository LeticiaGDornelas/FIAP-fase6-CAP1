<div align="center">

<a href="https://www.fiap.com.br/">
  <img alt="FIAP - Faculdade de Informática e Administração Paulista" src="assets/logo-fiap.png" width="160px">
</a>

</div>

<br>

# 🐄🐑 FarmTech Solutions — Visão Computacional para Monitoramento de Rebanho

## Grupo MultiAgents

---

## 👨‍🎓 Integrantes

- [Laura de Andrade Castilho — RM568507](https://www.linkedin.com/in/)
- [Leticia Grossi Dornelas — RM568172](https://www.linkedin.com/in/leticiagdornelas/)
- [Leonardo Borges Alves da Mota — RM566939](https://www.linkedin.com/in/leonardo-borges-alves-da-mota-649703177/)
- [Bernardo Naves Doti Avelar — RM566867](https://www.linkedin.com/in/bernardo-doti/)
- [David Eduardo da Silva Correia — RM567525](https://www.linkedin.com/in/eduardo-correia-29327631/)

---

## 👩‍🏫 Professores

### Tutor(a)
- Ana Cristina dos Santos

### Coordenador(a)
- [André Godoi Chiovato](https://www.linkedin.com/in/profandregodoi/)

---

## 📜 Descrição

Este projeto foi desenvolvido no âmbito da **Fase 6** do curso de Inteligência Artificial da FIAP, para a disciplina de Redes Neurais. O desafio simula um contexto real da **FarmTech Solutions** — empresa fictícia de consultoria em IA — que está expandindo seus serviços para o setor de **saúde animal e monitoramento de fazendas**.

O objetivo central foi construir um **sistema de visão computacional** capaz de detectar e classificar automaticamente dois animais típicos de fazenda: **vacas (cow)** e **ovelhas (sheep)**. O sistema foi desenvolvido com três abordagens distintas e comparadas entre si:

1. **YOLOv5 Customizado** — treinamento com fine-tuning em dataset específico de fazenda
2. **YOLO Padrão** — uso direto do modelo pré-treinado no COCO, sem customização
3. **CNN do Zero** — rede convolucional desenvolvida manualmente em PyTorch para classificação binária

O dataset utilizado é o **COCO 2017** (Microsoft), acessado via biblioteca FiftyOne, filtrado para as classes `cow` e `sheep` com 100 imagens públicas. As imagens foram convertidas para o formato YOLOv5 e divididas em treino, validação e teste.

Foram realizadas **duas simulações com épocas diferentes (30 e 60)** para o YOLOv5 customizado, comparando convergência, acurácia e desempenho. Ao final, uma análise crítica compara as três abordagens em termos de facilidade de uso, precisão, tempo de treino e tempo de inferência.

---

## 📁 Estrutura de Pastas

```
FIAP-fase6-CAP1/
├── .github/              # Configurações do GitHub
├── assets/               # Imagens e recursos visuais do projeto
│   ├── logo-fiap.png
│   ├── samples_dataset.png
│   ├── compare_30_60.png
│   ├── detections_test.png
│   ├── cnn_curves.png
│   └── comparison_chart.png
├── document/             # Documentos de apoio
├── src/                  # Código-fonte principal
│   └── GrupoMultiAgents_pbl_fase6.ipynb   ← NOTEBOOK PRINCIPAL
├── scripts/              # Scripts auxiliares
└── README.md             # Este arquivo
```

---

## 🗂️ Dataset

| Item | Detalhe |
|------|---------|
| **Fonte** | [COCO 2017 — Microsoft](https://cocodataset.org) via [FiftyOne Zoo](https://docs.voxel51.com/user_guide/dataset_zoo/datasets.html) |
| **Classes** | `cow` (vaca) e `sheep` (ovelha) |
| **Total de imagens** | 100 imagens (split de validação do COCO) |
| **Formato** | YOLOv5 PyTorch (.txt + data.yaml) |
| **Licença** | Público — CC BY 4.0 |

**Distribuição das imagens:**

| Split | Proporção | Total aprox. |
|-------|-----------|-------------|
| Treino | 80% | ~80 imagens |
| Validação | 10% | ~10 imagens |
| Teste | 10% | ~10 imagens |
| **Total** | **100%** | **100 imagens** |

---

## 🔧 Como Executar o Notebook

### Pré-requisitos
- Conta Google (para uso do Google Colab)
- GPU recomendada (Colab gratuito com T4 é suficiente — **não precisa de API key**)

### Passo a Passo

**1. Abrir o notebook no Google Colab**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LeticiaGDornelas/FIAP-fase6-CAP1/blob/main/src/GrupoMultiAgents_pbl_fase6.ipynb)

**2. Ativar GPU no Colab**

```
Menu: Ambiente de execução → Alterar tipo de ambiente de execução → GPU (T4)
```

**3. Executar todas as células em ordem**

```
Menu: Ambiente de execução → Executar tudo (Ctrl+F9)
```

O notebook executará automaticamente:
- Download do dataset COCO (cow + sheep) via FiftyOne
- Conversão para formato YOLOv5
- Treinamento YOLOv5 customizado (30 épocas)
- Treinamento YOLOv5 customizado (60 épocas)
- Inferência e validação
- Treinamento CNN do zero (30 épocas)
- Comparação e análise final

### Tempo estimado de execução total

| Etapa | Tempo (Colab T4) |
|-------|-----------------|
| Instalação + Download COCO | ~10 min |
| Treino YOLOv5 30 épocas | ~15 min |
| Treino YOLOv5 60 épocas | ~30 min |
| CNN do zero 30 épocas | ~10 min |
| **Total** | **~65 min** |

---

## 📊 Resultados Resumidos

### Ambiente de Execução
- **GPU:** Tesla T4
- **PyTorch:** 2.10.0+cu128
- **CUDA:** 13.0

### Comparação Final

| Critério | YOLOv5 Custom | YOLO Padrão | CNN do Zero |
|----------|:---:|:---:|:---:|
| Facilidade de uso | ★★★★☆ | ★★★★★ | ★★☆☆☆ |
| Precisão no domínio | Alta | Moderada | Moderada |
| Tempo de treino | ~30 min | Zero | ~10 min |
| Localiza objeto? | ✅ Sim | ✅ Sim | ❌ Não |
| Multi-objeto por frame? | ✅ Sim | ✅ Sim | ❌ Não |
| Precisa de API key? | ❌ Não | ❌ Não | ❌ Não |

---

## 🎥 Vídeo Demonstrativo

> 📹 Link do vídeo no YouTube (não listado): **[a ser inserido após gravação]**

---

## 🗃️ Histórico de Lançamentos

- 1.0.0 — Entrega Final Fase 6 (2025.2)
  - Dataset COCO 2017 (cow + sheep) via FiftyOne
  - YOLOv5 customizado (30 e 60 épocas)
  - YOLO padrão aplicado
  - CNN treinada do zero
  - Análise comparativa completa

---

## 📋 Licença

[![CC BY 4.0](https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1)](http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1)
[![BY](https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1)](http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1)

[MODELO GIT FIAP](https://github.com/agodoi/template) por [FIAP](https://fiap.com.br) está licenciado sob [Attribution 4.0 International](http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1).
