---
title: Ferramentas do Visual Studio para Docker no Windows
description: Obtenha as ferramentas do Docker disponíveis no Visual Studio 2017 versão 15.7 e posteriores de saber.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: d361b0c471402c097dfac799eb58ef08209d4343
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664367"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Use as ferramentas do Docker no Visual Studio 2017 no Windows

O fluxo de trabalho do desenvolvedor ao usar as ferramentas do Docker incluído no Visual Studio 2017 versão 15.7 e posteriores, é semelhante a usar o Visual Studio Code e CLI do Docker (na verdade, ele se baseia na mesma Docker CLI), mas ele é mais fácil de começar, simplifica o processo, e fornece maior produtividade para a compilação, executar e composição de tarefas. Ele também pode executar e depurar seus contêineres por meio de normais `F5` e `Ctrl+F5` teclas do Visual Studio. Você pode até mesmo depurar toda a solução se seus contêineres são definidos no mesmo `docker-compose.yml` arquivo no nível da solução.

## <a name="configure-your-local-environment"></a>Configurar seu ambiente local

Com as versões mais recentes do Docker para Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker porque a instalação é simples, conforme explicado nas seguintes referências.

> [!TIP]
> Para saber mais sobre como instalar o Docker para Windows, vá para (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Suporte do docker no Visual Studio 2017

Há dois níveis de suporte do Docker que você pode adicionar a um projeto. Em projetos do ASP.NET Core, você pode adicionar apenas um `Dockerfile` arquivo ao projeto, permitindo o suporte do Docker. O próximo nível é o suporte de orquestração de contêiner, que adiciona uma `Dockerfile` para o projeto (se ainda não existir) e um `docker-compose.yml` arquivo no nível da solução. Suporte de orquestração de contêiner, por meio do Docker Compose, é adicionado por padrão no Visual Studio 2017 versões 15.0 para 15.7. Suporte de orquestração de contêiner é um recurso de aceitação em versões do Visual Studio 2017 15,8 ou posteriores. Versão 15,8 um posteriormente oferecer suporte a Docker Compose e do Service Fabric.

O **Adicionar > suporte do Docker** e **Adicionar > suporte de orquestrador de contêiner** comandos estão localizados no menu de atalho (ou menu de contexto) do nó do projeto para um projeto ASP.NET Core em  **Gerenciador de soluções**, conforme mostrado na Figura 4-31:

![Adicionar a opção de menu de Suporte ao Docker no Visual Studio](./media/add-docker-support-menu.png)

**Figura 4-31**. Adicionando suporte ao Docker a um projeto do Visual Studio 2017

### <a name="add-docker-support"></a>Adicionar suporte ao Docker

Você pode adicionar suporte ao Docker a um projeto existente do ASP.NET Core, selecionando **Add** > **suporte ao Docker** na **Gerenciador de soluções**. Você também pode habilitar o suporte ao Docker durante a criação do projeto, selecionando **Habilitar suporte ao Docker** na **novo aplicativo Web do ASP.NET Core** caixa de diálogo que abre após você clicar em **Okey** no **novo projeto** caixa de diálogo, conforme mostrado na Figura 4-32.

![Habilitar o suporte ao Docker para o novo aplicativo Web do ASP.NET Core no Visual Studio](./media/enable-docker-support-visual-studio.png)

**Figura 4-32**. Habilitar o suporte ao Docker durante a criação do projeto no Visual Studio 2017

Quando você adiciona ou habilitar o suporte do Docker, o Visual Studio adiciona uma *Dockerfile* arquivo ao projeto.

> [!NOTE]
> Quando você habilita o suporte do Docker Compose durante a criação do projeto para um projeto do ASP.NET (.NET Framework, não em um projeto .NET Core) conforme mostrado na Figura 4-33, suporte de orquestração de contêiner também é adicionado.

![Habilitar o suporte ao Docker Compose para um projeto do ASP.NET](media/enable-docker-compose-support.png)

**Figura 4-33**. Habilitando o suporte do Docker Compose para um projeto ASP.NET no Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Adicionar suporte de orquestração de contêiner

Quando você deseja compor uma solução de vários contêiner, adicione suporte de orquestração de contêiner para seus projetos. Isso permite que você execute e depure um grupo de contêineres (uma solução inteira) ao mesmo tempo se eles estão definidos na mesma *docker-Compose. yml* arquivo.

Para adicionar suporte de orquestração de contêiner, clique com botão direito no nó do projeto ou solução na **Gerenciador de soluções**e escolha **Adicionar > suporte de orquestração de contêiner**. Em seguida, escolha **Docker Compose** ou **do Service Fabric** para gerenciar os contêineres.

Depois de adicionar suporte de orquestração de contêiner ao seu projeto, você verá um Dockerfile adicionado ao projeto e um **docker-compose** pasta adicionada à solução em **Gerenciador de soluções**, conforme mostrado na Figura 4-34:

![Arquivos do Docker no Gerenciador de Soluções no Visual Studio](media/docker-support-solution-explorer.png)

**Figura 4-34**. Arquivos do docker no Gerenciador de soluções no Visual Studio 2017

Se o *docker-compose.yml* já existir, o Visual Studio adiciona nele apenas as linhas necessárias do código de configuração.

## <a name="configure-docker-tools"></a>Configurar ferramentas do Docker

No menu principal, escolha **Ferramentas > Opções**e expanda **ferramentas de contêiner > configurações**. As configurações de ferramentas de contêiner aparecem.

![Docker no Visual Studio tools opções, que mostra: Extrair automaticamente as imagens necessárias do Docker no carregamento do projeto, iniciar automaticamente os contêineres em segundo plano, elimine automaticamente os contêineres no fechamento de solução e não solicitar para confiar em certificado SSL.](./media/visual-studio-docker-tools-options.png)

**Figura 4-35**. Opções de ferramentas do docker

A tabela a seguir pode ajudá-lo a decidir como definir essas opções.

| Nome | Configuração padrão | Aplica-se a | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Extrair automaticamente as imagens necessárias do Docker no carregamento do projeto | On | Docker Compose | Para melhorar o desempenho durante o carregamento de projetos, o Visual Studio será iniciado uma operação de pull do Docker em segundo plano para que quando você estiver pronto para executar seu código, a imagem é baixada já ou no processo de download. Se você estiver apenas carregar projetos e navegação de código, você pode desativar isso para evitar o download de imagens de contêiner, que você não precisa. |
| Iniciar automaticamente os contêineres em segundo plano | On | Docker Compose | Novamente para melhorar o desempenho, o Visual Studio cria um contêiner com montagens de volume pronto para quando você compila e executar seu contêiner. Se você desejar controlar quando o contêiner é criado, desative essa opção. |
| Fechar automaticamente os contêineres kill na solução | On | Docker Compose | Desative essa opção se você desejar contêineres para sua solução continuar a executar após fechar a solução ou fechar o Visual Studio. |
| Não solicitar certificado SSL localhost confiável | Off | Projetos do ASP.NET Core 2.2 | Se o certificado SSL do localhost não for confiável, Visual Studio solicitará que toda vez que você execute seu projeto, a menos que essa caixa de seleção está marcada. |

> [!WARNING]
> Se o certificado SSL do localhost não é confiável e você marcar a caixa para suprimir a solicitação, solicitações da web HTTPS podem falhar em tempo de execução em seu aplicativo ou serviço. Nesse caso, desmarque a **não solicitar** caixa de seleção, execute seu projeto e indicar confiança no prompt de.

> [!TIP]
> Para obter mais detalhes sobre a implementação de serviços e o uso de ferramentas do Visual Studio para Docker, leia os artigos a seguir:
>
>Depuração de aplicativos em um contêiner de Docker local: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Implante um contêiner ASP.NET em um registro de contêiner usando o Visual Studio: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Anterior](docker-apps-inner-loop-workflow.md)
>[Próximo](set-up-windows-containers-with-powershell.md)
