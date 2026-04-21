<div align="center">

<a href="https://www.fiap.com.br/">
 <img alt="FIAP - Faculdade de Informática e Administração Paulista" src="assets/logo-fiap (1).png" width="160px">
</a>

</div>

<br>

# FarmTech Solutions — Visão Computacional para Monitoramento de Rebanho

## Grupo MultiAgents

---

## 👨‍🎓 Integrantes

- [Laura de Andrade Castilho] — RM568507]
- [Leticia Grossi Dornelas — RM568172]
- [Leonardo Borges Alves da Mota — RM566939]
- [Bernardo Naves Doti Avelar — RM566867]
- [David Eduardo da Silva Correia — RM567525]

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

O dataset utilizado é público e disponível no Roboflow Universe ([Farm Animals — XDream](https://universe.roboflow.com/xdream/farm-animals-hv6qi)), com imagens de vacas e ovelhas já anotadas em formato YOLOv5.

Foram realizadas **duas simulações com épocas diferentes (30 e 60)** para o YOLOv5 customizado, comparando convergência, acurácia e desempenho. Ao final, uma análise crítica compara as três abordagens em termos de facilidade de uso, precisão, tempo de treino e tempo de inferência.

---

## 📁 Estrutura de Pastas

```
GrupoMultiAgents_fase6/
├── .github/              # Configurações do GitHub
├── assets/               # Imagens e recursos visuais do projeto
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
| **Fonte** | [Roboflow Universe — Farm Animals (XDream)](https://universe.roboflow.com/xdream/farm-animals-hv6qi) |
| **Classes** | `cow` (vaca) e `sheep` (ovelha) |
| **Formato** | YOLOv5 PyTorch (.txt + data.yaml) |
| **Licença** | Público (Roboflow Universe) |

**Distribuição das imagens:**

| Split | cow | sheep | Total |
|-------|-----|-------|-------|
| Treino | 32 | 32 | 64 |
| Validação | 4 | 4 | 8 |
| Teste | 4 | 4 | 8 |
| **Total** | **40** | **40** | **80** |

---

## 🔧 Como Executar o Notebook

### Pré-requisitos
- Conta Google (para uso do Google Colab)
- Conta gratuita no [Roboflow](https://app.roboflow.com) para obter a API key
- GPU recomendada (Colab gratuito com T4 é suficiente)

### Passo a Passo

**1. Abrir o notebook no Google Colab**

Clique no botão abaixo ou acesse diretamente:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SEU_USUARIO/GrupoMultiAgents_fase6/blob/main/src/GrupoMultiAgents_pbl_fase6.ipynb)

> ⚠️ Substitua `SEU_USUARIO` pelo nome do usuário GitHub do grupo após fazer o upload.

**2. Ativar GPU no Colab**

```
Menu: Ambiente de execução → Alterar tipo de ambiente de execução → GPU (T4)
```

**3. Obter API Key do Roboflow (gratuito)**

- Acesse [app.roboflow.com](https://app.roboflow.com)
- Vá em Settings → API Keys → copie sua chave
- Substitua `"YOUR_API_KEY"` na célula de download do dataset

**4. Executar todas as células em ordem**

```
Menu: Ambiente de execução → Executar tudo (Ctrl+F9)
```

O notebook executará automaticamente:
- Download do dataset
- Treinamento YOLOv5 (30 épocas)
- Treinamento YOLOv5 (60 épocas)
- Inferência e validação
- Treinamento CNN do zero
- Comparação e análise final

### Tempo estimado de execução total

| Etapa | Tempo (Colab T4) |
|-------|-----------------|
| Instalação + Download | ~5 min |
| Treino YOLOv5 30 épocas | ~15 min |
| Treino YOLOv5 60 épocas | ~30 min |
| CNN do zero 30 épocas | ~10 min |
| **Total** | **~60 min** |

---

## 📊 Resultados Resumidos

### YOLOv5 Customizado — 60 épocas (melhor modelo)

| Métrica | Valor |
|---------|-------|
| mAP@0.5 | ≥ 0.80 |
| Precisão | ≥ 0.85 |
| Recall | ≥ 0.80 |

### Comparação Final

| Critério | YOLOv5 Custom | YOLO Padrão | CNN do Zero |
|----------|:---:|:---:|:---:|
| Facilidade de uso | ★★★★☆ | ★★★★★ | ★★☆☆☆ |
| Precisão no domínio | Alta | Moderada | Moderada |
| Tempo de treino | ~30 min | Zero | ~10 min |
| Localiza objeto? | ✅ Sim | ✅ Sim | ❌ Não |
| Multi-objeto por frame? | ✅ Sim | ✅ Sim | ❌ Não |

---

## 🎥 Vídeo Demonstrativo

> 📹 Link do vídeo no YouTube (não listado): **[a ser inserido após gravação]**

---

## 🗃️ Histórico de Lançamentos

- 1.0.0 — Entrega Final Fase 6 (2025.2)
  - YOLOv5 customizado (30 e 60 épocas)
  - YOLO padrão aplicado
  - CNN treinada do zero
  - Análise comparativa completa

---

## 📋 Licença

[![CC BY 4.0](https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1)](http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1)
[![BY](https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1)](http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1)

[MODELO GIT FIAP](https://github.com/agodoi/template) por [FIAP](https://fiap.com.br) está licenciado sob [Attribution 4.0 International](http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1).
