---
title: Ferramentas do Visual Studio para Docker no Windows
description: Conheça as ferramentas disponíveis do Docker no Visual Studio 2017 versão 15.7 e posteriores.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644687"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Use as ferramentas do Docker no Visual Studio 2017 no Windows

O fluxo de trabalho do desenvolvedor ao usar as ferramentas do Docker, inclusas no Visual Studio 2017 versão 15.7 e posteriores, é semelhante a usar o Visual Studio Code e a CLI do Docker (na verdade, ele se baseia na mesma CLI do Docker), mas é mais fácil de começar a usar, simplifica o processo e fornece maior produtividade para criar, executar e compor tarefas. Ele também pode executar e depurar seus contêineres por meio das teclas `F5` e `Ctrl+F5` usuais do Visual Studio. Você poderá até mesmo depurar toda a solução se seus contêineres estiverem definidos no mesmo arquivo `docker-compose.yml` no nível da solução.

## <a name="configure-your-local-environment"></a>Configurar seu ambiente local

Com as versões mais recentes do Docker for Windows, é mais fácil do que nunca desenvolver aplicativos do Docker porque a instalação é simples, conforme explicado nas referências a seguir.

> [!TIP]
> Para saber mais sobre como instalar o Docker for Windows, confira (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Suporte ao Docker no Visual Studio 2017

Há dois níveis de suporte do Docker que você pode adicionar a um projeto. Em projetos do ASP.NET Core, você pode adicionar um arquivo `Dockerfile` ao projeto habilitando o suporte do Docker. O próximo nível é o suporte à orquestração de contêiner, que adiciona um `Dockerfile` ao projeto (caso ainda não exista) e um arquivo `docker-compose.yml` no nível da solução. O suporte à orquestração de contêiner, por meio do Docker Compose, é adicionado por padrão no Visual Studio 2017 versões 15.0 a 15.7. O suporte à orquestração de contêiner é um recurso de aceitação no Visual Studio 2017 versão 15.8 ou posteriores. A versão 15.8 e posteriores são compatíveis com o Docker Compose e o Service Fabric.

Os comandos **Adicionar > Suporte ao Docker** e **Adicionar > Suporte ao Orquestrador de Contêineres** estão localizados no menu de clique com o botão direito do mouse (ou menu de contexto) do nó do projeto para um projeto do ASP.NET Core no **Gerenciador de Soluções**, como mostrado na Figura 4-31:

![Adicionar a opção de menu de Suporte ao Docker no Visual Studio](./media/add-docker-support-menu.png)

**Figura 4-31**. Como adicionar suporte ao Docker a um projeto do Visual Studio 2017

### <a name="add-docker-support"></a>Adicionar suporte ao Docker

É possível adicionar suporte ao Docker a um projeto do ASP.NET Core existente ao selecionar **Adicionar** > **Suporte ao Docker** em **Gerenciador de Soluções**. Você também pode habilitar o suporte ao Docker durante a criação do projeto selecionando **Habilitar suporte ao Docker** na caixa de diálogo **Novo aplicativo Web do ASP.NET Core** que abre após você clicar em **OK** na caixa de diálogo **Novo Projeto**, conforme mostrado na Figura 4-32.

![Habilitar o suporte ao Docker para o novo aplicativo Web do ASP.NET Core no Visual Studio](./media/enable-docker-support-visual-studio.png)

**Figura 4-32**. Habilitar o suporte ao Docker durante a criação do projeto no Visual Studio 2017

Ao adicionar ou habilitar o suporte ao Docker, o Visual Studio adiciona um arquivo *Dockerfile* ao projeto.

> [!NOTE]
> Ao habilitar o suporte ao Docker Compose durante a criação do projeto em um projeto do ASP.NET (.NET Framework, não em um projeto do .NET Core), como mostrado na Figura 4-33, o suporte à orquestração de contêiner também é adicionado.

![Habilitar o suporte ao Docker Compose para um projeto do ASP.NET](media/enable-docker-compose-support.png)

**Figura 4-33**. Como habilitar o suporte ao Docker Compose para um projeto do ASP.NET no Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Adicionar suporte à orquestração de contêiner

Se você deseja compor uma solução de vários contêineres, adicione o suporte à orquestração de contêiner aos seus projetos. Isso permite que você execute e depure um grupo de contêineres (uma solução inteira) ao mesmo tempo, como se eles estivessem definidos no mesmo arquivo *docker-compose.yml*.

Para adicionar o suporte à orquestração de contêiner, clique com o botão direito do mouse no nó do projeto ou na solução no **Gerenciador de Soluções** e escolha **Adicionar > Suporte à orquestração de contêiner**. Em seguida, escolha **Docker Compose** ou **Service Fabric** para gerenciar os contêineres.

Depois de adicionar o suporte à orquestração de contêiner ao seu projeto, você verá um Dockerfile adicionado ao projeto e uma pasta **docker-compose** adicionada à solução no **Gerenciador de Soluções**, como mostrado na Figura 4-34:

![Arquivos do Docker no Gerenciador de Soluções no Visual Studio](media/docker-support-solution-explorer.png)

**Figura 4-34**. Arquivos do Docker no Gerenciador de Soluções no Visual Studio 2017

Se o *docker-compose.yml* já existir, o Visual Studio adiciona nele apenas as linhas necessárias do código de configuração.

## <a name="configure-docker-tools"></a>Configurar as ferramentas do Docker

No menu principal, escolha **Ferramentas > Opções** e expanda **Ferramentas de contêiner > Configurações**. As configurações de ferramentas de contêiner aparecem.

![Opções de ferramentas de Docker do Visual Studio, mostrando: Extração automática das imagens necessárias do Docker no carregamento do projeto, início automático dos contêineres em segundo plano, encerramento automático dos contêineres no fechamento da solução e Não solicitar para confiar no certificado SSL.](./media/visual-studio-docker-tools-options.png)

**Figura 4-35**. Opções de ferramentas do Docker

A tabela a seguir pode ajudá-lo a decidir como definir essas opções.

| Nome | Configuração Padrão | Aplica-se a | Descrição |
| -----|:---------------:|:----------:| ----------- |
| Extração automática das imagens necessárias do Docker no carregamento do projeto | On | Docker Compose | Para desempenho aprimorado durante o carregamento de projetos, o Visual Studio iniciará uma operação de pull do Docker em segundo plano para que, quando você estiver pronto para executar seu código, a imagem já esteja baixada ou sendo baixada. Se você estiver apenas carregando projetos e procurando código, será possível desativar isso para evitar o download de imagens de contêiner que você não precisa. |
| Início automático dos contêineres em segundo plano | On | Docker Compose | Novamente, para melhorar o desempenho, o Visual Studio cria um contêiner com montagens de volume prontas para quando você compilar e executar seu contêiner. Se você desejar controlar quando o contêiner é criado, desative essa opção. |
| Encerramento automático dos contêineres na solução | On | Docker Compose | Desative essa opção se desejar que os contêineres para sua solução continuem a executar após fechar a solução ou fechar o Visual Studio. |
| Não solicitar para confiar no certificado SSL do localhost | Off | Projetos do ASP.NET Core 2.2 | Se o certificado SSL do localhost não for confiável, o Visual Studio solicitará sempre que você executar seu projeto, a menos que esta caixa de seleção esteja marcada. |

> [!WARNING]
> Se o certificado SSL do localhost não for confiável e você marcar a caixa para suprimir a solicitação, as solicitações da Web HTTPS poderão falhar no tempo de execução em seu aplicativo ou serviço. Nesse caso, desmarque a caixa de seleção **Não solicitar**, execute seu projeto e indique a confiança no prompt.

> [!TIP]
> Para obter mais detalhes sobre a implementação dos serviços e o uso das Ferramentas do Visual Studio para Docker, leia os seguintes artigos:
>
>Depuração de aplicativos em um contêiner local do Docker: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Implantar um contêiner ASP.NET em um registro de contêiner usando o Visual Studio: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Anterior](docker-apps-inner-loop-workflow.md)
>[Próximo](set-up-windows-containers-with-powershell.md)
