---
title: Como instalar o Construtor de Modelo
description: Saiba como instalar a ferramenta Construtor de Modelo do ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: b944d7f6044553251132824e7e4213119e34500e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848646"
---
# <a name="how-to-install-mlnet-model-builder"></a>Como instalar o Construtor de Modelo do ML.NET

Saiba como instalar o Construtor de Modelo do ML.NET para adicionar o aprendizado de máquina aos seus aplicativos .NET.

> [!NOTE]
> O Construtor de Modelo está atualmente na Versão Prévia.

## <a name="prerequisites"></a>Pré-requisitos

- Visual Studio 2017 versão 15.9.12 ou posterior / Visual Studio 2019
- .NET Core 2.1 SDK ou posterior.

> [!NOTE]
> O SDK .NET Core 3.0 não é suportado no momento.

## <a name="limitations"></a>Limitações

- Extensão do Construtor de Modelo do ML.NET atualmente só funciona no Visual Studio no Windows.
- Limite de conjunto de dados de treinamento de 1GB
- O SQL Server tem um limite de 100 mil linhas para treinamento
- Não há suporte para Microsoft SQL Server Data Tools para Visual Studio 2017

## <a name="install"></a>Instalar

O Construtor de Modelo do ML.NET pode ser instalado por meio do Visual Studio Marketplace ou pelo Visual Studio.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

1. Baixe pelo [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)
1. Siga os prompts para instalar a respectiva versão do Visual Studio

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na barra de menus, selecione**Extensões e Atualizações de** **Ferramentas** > 

    ![Diálogo do gerenciador de extensões abertas VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, selecione o nó *Online*.
1. Na barra de pesquisa, busque por *Construtor de Modelo do ML.NET* e, nos resultados, selecione o Construtor de Modelo do ML.NET (Versão prévia)

    ![VS2017 pesquisa e instala extensão Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2017-install-model-builder.png)

1. Siga as instruções para concluir a instalação

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na barra de menu, selecione **Extensões** > **Gerenciar extensões**

    ![Diálogo do gerenciador de extensões abertas VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, selecione o nó *Online*.
1. Digite *Construtor de Modelo do ML.NET* na barra de pesquisa, selecione o Construtor do Modelo do ML.NET (Versão prévia)

    ![VS2019 pesquisa e instala extensão Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2019-install-model-builder.png)

1. Siga as instruções para concluir a instalação

## <a name="uninstall"></a>Desinstalar

### <a name="visual-studio-2017"></a>Visual Studio 2017

1. Na barra de menus, selecione**Extensões e Atualizações de** **Ferramentas** > 

    ![Diálogo de extensões de gerenciamento aberto VS2017](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*
1. Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*

    ![VS2017 pesquisa e desinstala extensão do Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. Siga as instruções para concluir a desinstalação.

### <a name="visual-studio-2019"></a>Visual Studio 2019

1. Na barra de menu, selecione **Extensões** > **Gerenciar extensões**

    ![Diálogo de extensões de gerenciamento aberto VS2019](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. No prompt *Extensões e Atualizações*, expanda o nó *Instalado* e selecione *Ferramentas*
1. Selecione o Construtor de Modelo do ML.NET (Versão prévia) na lista de ferramentas e depois selecione *Desinstalar*

    ![VS2019 pesquisa e desinstala extensão do Model Builder na caixa de diálogo gerenciador de extensões](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. Siga as instruções para concluir a desinstalação.

## <a name="upgrade"></a>Atualizar

O processo de atualização é semelhante ao processo de instalação. Baixe a versão mais recente do Visual Studio Marketplace ou use o Gerenciador de Extensões no Visual Studio.
