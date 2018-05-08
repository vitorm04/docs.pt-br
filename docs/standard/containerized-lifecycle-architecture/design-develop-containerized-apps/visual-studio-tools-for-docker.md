---
title: Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 05db5cf8e8dc073dd341fbffab619c326b48f136
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)

O fluxo de trabalho do desenvolvedor ao usar o Visual Studio Tools para o Docker é semelhante ao fluxo de trabalho ao usar o código do Visual Studio e a CLI do Docker (na verdade, ele se baseia a mesma CLI do Docker), mas é mais fácil de começar, simplifica o processo e fornece maior produtividade para a compilação, execução e compor tarefas. Também é possível executar e depurar seus contêineres por meio de ações simples, como F5 e Ctrl + F5 no Visual Studio. Ainda mais, com Visual 2017 Studio, além de poder executar e depurar um único contêiner, você também pode executar e depurar um grupo de contêineres (uma solução inteira) ao mesmo tempo, se eles são definidos no mesmo arquivo de docker compose.yml no nível da solução.

## <a name="configuring-your-local-environment"></a>Configurando seu ambiente local

Com as versões mais recentes do Docker para Windows, é mais fácil do que nunca para desenvolver aplicativos de Docker porque a instalação é simples, conforme explicado nas seguintes referências.

**Obter mais informações:** para saber mais sobre como instalar o Docker para Windows, acesse <https://docs.docker.com/docker-for-windows/>.

Se você estiver usando o Visual Studio 2015, você deve ter a atualização 3 ou uma versão posterior e o Visual Studio Tools para o Docker.

**Obter mais informações:** para obter instruções sobre como instalar o Visual Studio, vá para [ https://www.visualstudio.com/\ produtos/vs-2015-produto-edições](https://www.visualstudio.com/products/vs-2015-product-editions).

Para obter mais informações sobre como instalar o Visual Studio Tools para o Docker, vá para <http://aka.ms/vstoolsfordocker> e <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.

Se você estiver usando o Visual Studio de 2017, o suporte de Docker já está incluído.

## <a name="using-docker-tools-in-visual-studio-2015"></a>Usando ferramentas do Docker no Visual Studio 2015

O Visual Studio Tools para o Docker fornece uma maneira consistente para desenvolver e validar localmente os contêineres de Docker para Linux em um host Linux Docker ou VM ou os contêineres do Windows diretamente no Windows.

Se você estiver usando um único contêiner, a primeira coisa que você precisa para começar é ativar o suporte de Docker em seu projeto .NET Core. Para fazer isso, clique em seu arquivo de projeto, conforme mostrado na Figura 4-25.

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

Figura 4-25: ativar o suporte de Docker para o seu projeto do Visual Studio

## <a name="using-docker-tools-in-visual-studio-2017"></a>Usando ferramentas do Docker no Visual Studio de 2017

Quando você adiciona suporte de Docker para um projeto de serviço em sua solução (consulte a Figura 4-26), o Visual Studio é não apenas adicionar um arquivo de DockerFile ao seu projeto, ele também está adicionando uma seção de serviço em sua solução docker compose.yml arquivos (ou criar os arquivos se eles não Existem). É uma maneira fácil de começar a composição de sua solução multicontainer; Você pode abrir os arquivos de docker compose.yml e atualizá-los com recursos adicionais.

![](./media/image32.png)

Figura 4-26: ativar o suporte de solução de Docker em um projeto do Visual Studio de 2017

Essa ação adiciona não apenas o DockerFile ao seu projeto, ele também adiciona linhas de código para a configuração necessária para um docker-compose.yml global definida no nível da solução.

Você também pode ativar o suporte do Docker ao criar um projeto do ASP.NET Core no Visual Studio de 2017, conforme mostrado na Figura 4-27.

![](./media/image33.png)

Figura 4-27: ativar o suporte do Docker ao criar um projeto

Depois de adicionar suporte de Docker para sua solução no Visual Studio, você também verá uma nova árvore de nó no Gerenciador de soluções, com os arquivos de inclusão docker-compose.yml, conforme ilustrado na Figura 4-28.

![](./media/image34.PNG)

Figura 4-28: arquivos de docker compose.yml agora exibidos no Gerenciador de soluções

Você pode implantar um multicontainer aplicativo usando um arquivo único docker-compose.yml quando você executa compor docker. No entanto, o Visual Studio adiciona um grupo, para que você pode substituir valores de acordo com o ambiente (desenvolvimento e produção) e a execução de tipo (versão versus depuração). Esse recurso será explicado melhor capítulos.

**Obter mais informações:** para obter mais detalhes sobre o uso de ferramentas do Visual Studio para Docker e a implementação de serviços, leia os seguintes artigos:

Compilar, depurar, atualizar e atualizar aplicativos em um contêiner de Docker local: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Implante um contêiner do ASP.NET em um host remoto do Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)


>[!div class="step-by-step"]
[Anterior] (docker-aplicativos-interna-loop-workflow.md) [Avançar] (set-up-windows-containers-with-powershell.md)
