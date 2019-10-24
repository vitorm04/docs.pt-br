---
title: Como instalar o Construtor de Modelo
description: Saiba como instalar a ferramenta Construtor de Modelo do ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774563"
---
# <a name="how-to-install-mlnet-model-builder"></a>Como instalar o Construtor de Modelo do ML.NET

Saiba como instalar o Construtor de Modelo do ML.NET para adicionar o aprendizado de máquina aos seus aplicativos .NET.

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="pre-requisites"></a>Pré-requisitos

- Visual Studio 2017 versão 15.9.12 ou posterior/Visual Studio 2019
- SDK do .NET core 2.1 ou posterior

## <a name="limitations"></a>Limitações

- Extensão do Construtor de Modelo do ML.NET atualmente só funciona no Visual Studio no Windows.
- Limite de conjunto de dados de treinamento de 1GB
- O SQL Server tem um limite de 100 mil linhas para treinamento
- Não há suporte para Microsoft SQL Server Data Tools para Visual Studio 2017

## <a name="install"></a>Instalar o

O Construtor de Modelo do ML.NET pode ser instalado por meio do Visual Studio Marketplace ou pelo Visual Studio.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Baixe pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Siga os prompts para instalar a respectiva versão do Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**

    ![Caixa de diálogo VS2017 Open Extensions Manager](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, selecione o nó *Online*.
1. Na barra de pesquisa, busque por *Construtor de Modelo do ML.NET* e, nos resultados, selecione o Construtor de Modelo do ML.NET (Versão prévia)

    ![VS2017 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-install-model-builder.png)

1. Siga as instruções para concluir a instalação

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**

    ![Caixa de diálogo VS2019 Open Extensions Manager](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, selecione o nó *Online*.
1. Digite *Construtor de Modelo do ML.NET* na barra de pesquisa, selecione o Construtor do Modelo do ML.NET (Versão prévia)

    ![VS2019 pesquisa e instale a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-install-model-builder.png)

1. Siga as instruções para concluir a instalação

## <a name="uninstall"></a>Desinstalar

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na barra de menus, selecione **Ferramentas** > **Extensões e Atualizações**

    ![VS2017 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*
1. Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*

    ![VS2017 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Siga as instruções para concluir a desinstalação.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na barra de menus, selecione **Extensões** > **Gerenciar Extensões**

    ![VS2019 abrir a caixa de diálogo Gerenciar extensões](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*
1. Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*

    ![VS2019 Pesquisar e desinstalar a extensão do construtor de modelos na caixa de diálogo Gerenciador de extensões](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Siga as instruções para concluir a desinstalação.

## <a name="upgrade"></a>Atualização

O processo de atualização é semelhante ao processo de instalação. Baixe a versão mais recente do Visual Studio Marketplace ou use o Gerenciador de Extensões no Visual Studio.
