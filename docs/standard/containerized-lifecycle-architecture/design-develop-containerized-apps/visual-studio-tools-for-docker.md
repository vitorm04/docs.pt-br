---
title: Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46516737"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)

O fluxo de trabalho de desenvolvimento ao usar ferramentas do Visual Studio para Docker é semelhante ao fluxo de trabalho ao usar o Visual Studio Code e CLI do Docker. Na verdade, ele se baseia a CLI do Docker mesmo, mas é mais fácil de começar, simplifica o processo e fornece maior produtividade para a compilação, executar e composição de tarefas. Também é capaz de executar e depurar seus contêineres por meio de ações simples, como F5 e Ctrl + F5 no Visual Studio. Com o suporte de orquestração de contêiner opcional, além de poder executar e depurar um único contêiner, você pode executar e depurar um grupo de contêineres (uma solução inteira) ao mesmo tempo. Basta definir os contêineres no mesmo *docker-Compose. yml* arquivo no nível da solução.

## <a name="configuring-your-local-environment"></a>Configurando seu ambiente local

Suporte ao docker está incluído no Visual Studio 2017 com qualquer uma das cargas de trabalho do .NET e .NET Core instaladas. Instale o Docker para Windows separadamente.

Com as versões mais recentes do Docker para Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker porque a instalação é simples, conforme explicado nas seguintes referências.

**Obter mais informações:** para saber mais sobre como instalar o Docker para Windows, vá para <https://docs.docker.com/docker-for-windows/>.

**Obter mais informações:** para obter instruções sobre como instalar o Visual Studio, acesse [ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/).

Para obter mais informações sobre como instalar as ferramentas do Visual Studio para Docker, vá para <http://aka.ms/vstoolsfordocker> e <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.

## <a name="using-docker-tools-in-visual-studio-2017"></a>Usando as ferramentas do Docker no Visual Studio 2017

Ao adicionar suporte ao Docker a um projeto (consulte a Figura 4-26), o Visual Studio adiciona uma *Dockerfile* à raiz do projeto.

![Ativar o suporte da solução do Docker em um projeto do Visual Studio 2017](./media/image32.png)

Figura 4-26: ativar o suporte da solução do Docker em um projeto do Visual Studio 2017

 Suporte de orquestração de contêiner, por meio do Docker Compose, é adicionado por padrão nas versões do Visual Studio 2017 15.7 ou anteriores. Suporte de orquestração de contêiner é um recurso de aceitação em versões do Visual Studio 2017 15,8 ou posterior, nesse caso, Docker Compose e o Service Fabric têm suporte.

Com o Visual Studio versão 15,8 e posterior, você pode adicionar suporte para vários projetos em uma solução que possuem um contêiner associado. Clique com botão direito no nó do projeto ou solução na **Gerenciador de soluções**e escolha **Add** > **suporte de orquestração de contêiner**.  Em seguida, escolha **Docker Compose** ou **do Service Fabric** para gerenciar os contêineres.

Quando você escolhe **Docker Compose**, o Visual Studio adiciona uma seção de serviço em sua solução *docker-Compose. yml* arquivos (ou cria os arquivos se não existirem). É uma maneira fácil de começar a compor sua solução de vários contêiner; Você pode abrir o *docker-Compose. yml* arquivos e atualizá-los com recursos adicionais.

Essa ação adiciona as linhas de configuração necessárias de código para um *docker-Compose. yml* definido no nível da solução.

Você também pode ativar o suporte do Docker ao criar um projeto ASP.NET Core no Visual Studio 2017, conforme mostrado na Figura 4-27.

![Ativar o suporte do Docker ao criar um projeto](./media/image33.png)

Figura 4-27: ativar o suporte do Docker ao criar um projeto

Depois de adicionar suporte ao Docker à sua solução no Visual Studio, você também verá uma nova árvore de nós em **Gerenciador de soluções** com a adição *docker-Compose. yml* arquivos, conforme ilustrado na Figura 4-28.

![arquivos docker-Compose. yml agora são exibidos no Gerenciador de soluções](./media/image34.PNG)

Figura 4-28: arquivos docker-Compose. yml agora são exibidos em **Gerenciador de soluções**

Você pode implantar um aplicativo de vários contêiner usando um único *docker-Compose. yml* arquivo quando você executar `docker-compose up`; no entanto, o Visual Studio adiciona um grupo desses arquivos, para que você pode substituir valores dependendo do ambiente (desenvolvimento versus produção) e a execução (lançamento versus depuração) de tipo. Essa funcionalidade é explicada melhor nos próximos capítulos.

Você também pode usar o Service Fabric, em vez de Docker Compose para gerenciar vários contêineres. Ver [Tutorial: implantar um aplicativo .NET em um contêiner do Windows no Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).

**Obter mais informações:** para obter mais detalhes sobre a implementação de serviços e o uso de ferramentas do Visual Studio para Docker, leia os artigos a seguir:

Compilar, depurar, atualizar e atualizar aplicativos em um contêiner de Docker local: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Implante um contêiner de docker do ASP.NET Core em um registro de contêiner: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
[Anterior](docker-apps-inner-loop-workflow.md)
[Próximo](set-up-windows-containers-with-powershell.md)
