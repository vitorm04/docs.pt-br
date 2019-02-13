---
title: Ferramentas do Visual Studio para Docker no Windows
description: Obtenha as ferramentas do Docker disponíveis no Visual Studio 2017 versão 15.7 e posteriores de saber.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.custom: vs-dotnet
ms.openlocfilehash: a373a8ebfef605b9845a684d3987355f8841aa1b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219536"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Usando ferramentas do Visual Studio para Docker (Visual Studio no Windows)

O Visual Studio Tools para o fluxo de trabalho de desenvolvimento de Docker é semelhante ao fluxo de trabalho ao usar o Visual Studio Code e CLI do Docker. Na verdade, ele se baseia a CLI do Docker mesmo, mas é mais fácil de começar, simplifica o processo e fornece maior produtividade para a compilação, executar e composição de tarefas. Executar e depurar seus contêineres por meio de ações simples, como **F5** e **Ctrl**+**F5**. Com o suporte de orquestração de contêiner opcional, além de poder executar e depurar um único contêiner, você pode executar e depurar um grupo de contêineres (uma solução inteira) ao mesmo tempo.

> [!NOTE]
> Este artigo se aplica ao Visual Studio no Windows e não no Visual Studio para Mac.

## <a name="configure-your-local-environment"></a>Configurar seu ambiente local

Com as versões mais recentes do Docker para Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), o programa de instalação simples torna mais fácil desenvolver aplicativos do Docker.

Suporte ao docker está incluído no Visual Studio 2017. Baixe o Visual Studio 2017 aqui: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="use-docker-tools-in-visual-studio-2017"></a>Use as ferramentas do Docker no Visual Studio 2017

Há dois níveis de suporte do Docker que você pode adicionar a um projeto. Em projetos de aplicativo web .NET Core, você pode adicionar apenas um *Dockerfile* arquivo ao projeto, permitindo o suporte do Docker. O próximo nível é o suporte de orquestração de contêiner, que adiciona uma *Dockerfile* para o projeto (se ainda não existir) e uma *docker-Compose. yml* arquivo no nível da solução. Suporte de orquestração de contêiner, por meio do Docker Compose, é adicionado por padrão nas versões do Visual Studio 2017 15.7 ou anteriores. Suporte de orquestração de contêiner é um recurso de aceitação em versões do Visual Studio 2017 15,8 ou posterior, nesse caso, Docker Compose e o Service Fabric têm suporte.

O **Add** > **suporte ao Docker** e **Add** > **suporte de orquestração de contêiner** comandos são localizado no menu de atalho (ou menu de contexto) do nó do projeto para um projeto de aplicativo web no **Gerenciador de soluções**, conforme mostrado na Figura 4-26:

![Adicionar a opção de menu de suporte do Docker no Visual Studio](media/add-docker-support-menu.png)

Figura 4-26: Adicionando suporte ao Docker a um projeto do Visual Studio 2017

### <a name="add-docker-support"></a>Adicionar suporte ao Docker

Você pode adicionar suporte ao Docker para um projeto de aplicativo web .NET Core existente selecionando **Add** > **suporte ao Docker** na **Gerenciador de soluções**. Você também pode habilitar o suporte ao Docker durante a criação do projeto, selecionando **Habilitar suporte ao Docker** na **novo aplicativo Web do ASP.NET Core** caixa de diálogo que abre após você clicar em **Okey** no **novo projeto** caixa de diálogo, conforme mostrado na Figura 4-27.

![Habilitar o suporte do Docker para o novo aplicativo web de ASP.NET Core no Visual Studio](./media/enable-docker-support-visual-studio.png)

Figura 4-27: Habilitar o suporte ao Docker durante a criação do projeto no Visual Studio 2017

Quando você adiciona ou habilitar o suporte do Docker, o Visual Studio adiciona uma *Dockerfile* arquivo ao projeto.

> [!NOTE]
> Quando você habilita o suporte do Docker Compose durante a criação do projeto para um projeto de aplicativo web do .NET Framework (não um projeto de aplicativo .NET Core da web) como mostrado na Figura 4-28, suporte de orquestração de contêiner também é adicionado.
>
> ![Habilitar o Docker compose suporte para um projeto de aplicativo web do .NET Framework](media/enable-docker-compose-support.png)

> Figura 4-28: Habilitando o suporte do Docker Compose em um projeto de aplicativo web do .NET Framework no Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Adicionar suporte de orquestração de contêiner

Quando você deseja compor uma solução de vários contêineres, adicione suporte de orquestração de contêiner para seus projetos. Isso permite que você execute e depure um grupo de contêineres (uma solução inteira) ao mesmo tempo se eles estão definidos na mesma *docker-Compose. yml* arquivo.

Para adicionar suporte de orquestração de contêiner, clique com botão direito no nó do projeto ou solução na **Gerenciador de soluções**e escolha **Add** > **suporte de orquestração de contêiner**. Em seguida, escolha **Docker Compose** ou **do Service Fabric** para gerenciar os contêineres.

Depois de adicionar suporte de orquestração de contêiner ao seu projeto, você verá um Dockerfile adicionado ao projeto e um **docker-compose** pasta adicionada à solução em **Gerenciador de soluções**, conforme mostrado na Figura 4-29:

![Arquivos do docker no Gerenciador de soluções no Visual Studio](media/docker-support-solution-explorer.png)

Figura 4-29: Arquivos do docker no Gerenciador de soluções no Visual Studio 2017

Se *docker-Compose. yml* já existir, o Visual Studio adiciona apenas as linhas necessárias de código de configuração a ele.

## <a name="configure-docker-tools"></a>Configurar ferramentas do Docker

No menu principal, escolha **ferramentas** > **opções**e expanda **ferramentas de contêiner** > **configurações**. As configurações de ferramentas de contêiner aparecem.

![](./media/visual-studio-docker-tools-options.png)

Figura 4-30: Opções de ferramentas do docker

A tabela a seguir pode ajudá-lo a decidir como definir essas opções.

| Nome | Configuração padrão | Aplica-se a | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Extrair automaticamente as imagens necessárias do Docker no carregamento do projeto | On | Docker Compose | Para melhorar o desempenho, ao carregar projetos, o Visual Studio será iniciado uma operação de pull do Docker em segundo plano para que quando você estiver pronto para executar seu código, a imagem é baixada já ou no processo de download. Se você estiver apenas carregar projetos e navegação de código, você pode desativar isso para evitar o download de imagens de contêiner, que você não precisa. |
| Iniciar automaticamente os contêineres em segundo plano | On | Docker Compose | Novamente para melhorar o desempenho, o Visual Studio cria um contêiner com montagens de volume pronto para quando você compila e executar seu contêiner. Se você desejar controlar quando o contêiner é criado, desative essa opção. |
| Fechar automaticamente os contêineres kill na solução | On | Docker Compose | Desative essa opção se você desejar contêineres para sua solução continuar a executar após fechar a solução ou fechar o Visual Studio. |
| Não solicitar certificado SSL localhost confiável | Off | Projetos do ASP.NET Core 2.1 | Se o certificado SSL do localhost não for confiável, Visual Studio solicitará que toda vez que você execute seu projeto, a menos que essa caixa de seleção está marcada. |

> [!WARNING]
> Se o certificado SSL do localhost não é confiável e você marcar a caixa para suprimir a solicitação, solicitações da web HTTPS podem falhar em tempo de execução em seu aplicativo ou serviço. Nesse caso, desmarque a **não solicitar** caixa de seleção, execute seu projeto e indicar confiança no prompt de.

**Obter mais informações:** para obter mais detalhes sobre a implementação de serviços e o uso de ferramentas do Visual Studio para Docker, leia os artigos a seguir:

Compilar, depurar, atualizar e atualizar aplicativos em um contêiner de Docker local: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Implante um contêiner de docker do ASP.NET Core em um registro de contêiner: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

>[!div class="step-by-step"]
>[Anterior](docker-apps-inner-loop-workflow.md)
>[Próximo](set-up-windows-containers-with-powershell.md)