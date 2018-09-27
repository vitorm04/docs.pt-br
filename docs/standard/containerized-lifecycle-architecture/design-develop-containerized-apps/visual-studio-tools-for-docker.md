---
title: Ferramentas do Visual Studio para Docker no Windows
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235709"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)

O Visual Studio Tools para o fluxo de trabalho de desenvolvedor de Docker é semelhante a usar o Visual Studio Code e CLI do Docker (ele se baseia a CLI do Docker mesmo). Ferramentas do Visual Studio para Docker facilita ainda mais começar, simplifica o processo e fornece maior produtividade para a compilação, executar e composição de tarefas. Executar e depurar seus contêineres por meio de ações simples, como **F5** e **Ctrl**+**F5**.

> [!NOTE]
> Este artigo se aplica ao Visual Studio no Windows e não no Visual Studio para Mac.

## <a name="configure-your-local-environment"></a>Configurar seu ambiente local

Com as versões mais recentes do Docker para Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), o programa de instalação simples torna mais fácil desenvolver aplicativos do Docker.

Suporte ao docker está incluído no Visual Studio 2017. Baixe o Visual Studio 2017 aqui: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Use as ferramentas do Docker no Visual Studio 2017

Há dois níveis de suporte do Docker que você pode adicionar a um projeto. Em projetos de aplicativo web .NET Core, você pode adicionar apenas um *Dockerfile* arquivo ao projeto, permitindo o suporte do Docker. O próximo nível é o suporte de orquestrador de contêiner, que adiciona uma *Dockerfile* para o projeto (se ainda não existir) e uma *docker-Compose. yml* arquivo no nível da solução.

O **Add** > **suporte ao Docker** e **Add** > **suporte de orquestrador de contêiner** comandos são localizado no menu de atalho (ou menu de contexto) do nó do projeto para um projeto de aplicativo web no **Gerenciador de soluções**, conforme mostrado na Figura 4-26:

![Adicionar a opção de menu de suporte do Docker no Visual Studio](media/add-docker-support-menu.png)

Figura 4-26: adicionar suporte ao Docker a um projeto do Visual Studio 2017

### <a name="add-docker-support"></a>Adicionar suporte ao Docker

Você pode adicionar suporte ao Docker para um projeto de aplicativo web .NET Core existente selecionando **Add** > **suporte ao Docker** na **Gerenciador de soluções**. Você também pode habilitar o suporte ao Docker durante a criação do projeto, selecionando **Habilitar suporte ao Docker** na **novo aplicativo Web do ASP.NET Core** caixa de diálogo que abre após você clicar em **Okey** no **novo projeto** caixa de diálogo, conforme mostrado na Figura 4-27.

![Habilitar o suporte do Docker para o novo aplicativo web de ASP.NET Core no Visual Studio](./media/enable-docker-support-visual-studio.png)

Figura 4-27: habilitar o suporte ao Docker durante a criação do projeto no Visual Studio 2017

Quando você adiciona ou habilitar o suporte do Docker, o Visual Studio adiciona uma *Dockerfile* arquivo ao projeto.

> [!NOTE]
> Quando você habilita o suporte do Docker Compose durante a criação do projeto para um projeto de aplicativo web do .NET Framework (não um projeto de aplicativo .NET Core da web) como mostrado na Figura 4-28, suporte de orquestrador de contêiner também é adicionado.
>
> ![Habilitar o Docker compose suporte para um projeto de aplicativo web do .NET Framework](media/enable-docker-compose-support.png)

> Figura 4-28: Habilitando o suporte do Docker Compose em um projeto de aplicativo web do .NET Framework no Visual Studio 2017

### <a name="add-container-orchestrator-support"></a>Adicionar suporte de orquestrador de contêiner

Quando você deseja compor uma solução de vários contêineres, adicione suporte de orquestrador de contêiner para seus projetos. Quando você adiciona suporte de orquestrador de contêiner, o Visual Studio adiciona uma *Dockerfile* ao projeto (se ainda não existir) e um global *docker-Compose. yml* arquivo no nível da solução. Isso permite que você execute e depure um grupo de contêineres (uma solução inteira) ao mesmo tempo se eles estão definidos na mesma *docker-Compose. yml* arquivo. Se *docker-Compose. yml* já existir, o Visual Studio adiciona apenas as linhas necessárias de código de configuração a ele.

Depois de adicionar suporte de orquestração de contêiner ao seu projeto, você verá um Dockerfile adicionado ao projeto e um **docker-compose** pasta adicionada à solução em **Gerenciador de soluções**, conforme mostrado na Figura 4-29:

![Arquivos do docker no Gerenciador de soluções no Visual Studio](media/docker-support-solution-explorer.png)

Figura 4-29: arquivos do Docker no Gerenciador de soluções no Visual Studio 2017

**Obter mais informações:** para obter mais detalhes sobre a implementação de serviços e o uso de ferramentas do Visual Studio para Docker, leia os artigos a seguir:

Compilar, depurar, atualizar e atualizar aplicativos em um contêiner de Docker local: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Implante um contêiner de docker do ASP.NET Core em um registro de contêiner: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Anterior](docker-apps-inner-loop-workflow.md)
[Próximo](set-up-windows-containers-with-powershell.md)