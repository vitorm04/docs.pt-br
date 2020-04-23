---
title: Ferramentas para desenvolvedores .NET do Azure e .NET Core
description: Obtenha as ferramentas para começar a usar as bibliotecas .NET do Azure em um ambiente Windows, Linux ou Mac.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071937"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a>Ferramentas para desenvolvedores .NET e .NET Core do Azure

## <a name="sdk-downloads"></a>Downloads do SDK

As bibliotecas do Azure para .NET são implementadas como [pacotes NuGet](https://www.nuget.org/packages?q=windowsazureofficial). Consulte a [referência de API](/dotnet/api/overview/azure/?view=azure-dotnet) para obter instruções de instalação organizadas pelo serviço do Azure.

## <a name="development-tools"></a>Ferramentas de desenvolvimento

O Visual Studio tem ferramentas para muitos serviços do Azure internos. Alguns serviços do Azure têm ferramentas ou emuladores adicionais disponíveis, como [Gerenciador de armazenamento do Azure](https://azure.microsoft.com/features/storage-explorer/). Consulte a documentação do serviço do Azure para obter outras ferramentas, se necessário.

Estas instruções instalam o ambiente de desenvolvimento inicial recomendado para seu sistema operacional.

## <a name="windows"></a>[Windows](#tab/windows)

As versões 2017 e posteriores do Visual Studio têm suporte interno para o desenvolvimento do Azure. As etapas a seguir descrevem a habilitação do suporte de desenvolvimento do Azure no Visual Studio.

Para o Visual Studio 2015 e anterior, <a href="vs2015-install.md">siga estas instruções</a>.

### <a name="step-1-download-visual-studio-2019"></a>Etapa 1: baixar o Visual Studio 2019

Você pode ignorar esta etapa se já tiver o Visual Studio 2019 instalado.

> [!div class="nextstepaction"]
> [Baixar o Visual Studio 2019](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a>Etapa 2: instalar as duas cargas de trabalho do Azure

No instalador do Visual Studio, instale o Visual Studio (ou modifique uma instalação existente). Verifique se as cargas de trabalho *desenvolvimento do Azure* e *ASP.net e desenvolvimento Web* estão selecionadas.

### <a name="step-3-develop-with-net-on-azure"></a>Etapa 3: desenvolver com o .NET no Azure

Comece [implantando seu primeiro aplicativo Web ASP.NET Core no Serviço de Aplicativo do Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).

## <a name="macos"></a>[macOS](#tab/macos)

O Visual Studio para Mac tem tudo o que você precisa para desenvolvimento do Azure.

### <a name="step-1-download-visual-studio-for-mac"></a>Etapa 1: baixar o Visual Studio para Mac

> [!div class="nextstepaction"]
> [Baixar o Visual Studio para Mac](https://www.visualstudio.com/vs/visual-studio-mac/)

Durante a instalação, as ferramentas do Azure são selecionadas por padrão.

## <a name="linux"></a>[Linux](#tab/linux)

O Visual Studio Code tem tudo o que você precisa para desenvolvimento do Azure no Linux.

### <a name="step-1-download-the-net-core-sdk"></a>Etapa 1: Baixar o SDK do .NET Core

O SDK e as ferramentas de linha de comando para aplicativos .NET Core.

> [!div class="nextstepaction"]
> [Baixar o SDK do .NET Core](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a>Etapa 2: Visual Studio Code

Edite e depure aplicativos .NET Core em qualquer sistema operacional: Windows, Mac e Linux.

> [!div class="nextstepaction"]
> [Baixar o Visual Studio Code](https://code.visualstudio.com)

---
