---
title: Processo de desenvolvimento do Azure
description: Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Processo de desenvolvimento do Azure
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 21826e2c90d234d873cc06bfae3bd22ce89a62d2
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="development-process-for-azure"></a>Processo de desenvolvimento do Azure

> _"Com a nuvem, pessoas e pequenas empresas podem ajustar seus dedos e instantaneamente configurar serviços de classe empresarial."_  
> _-Roy Stephan_

 ## <a name="vision"></a>Visão

> *Desenvolva aplicativos de ASP .NET Core bem projetados da maneira desejada, usando o Visual Studio ou o CLI dotnet e código do Visual Studio ou o editor escolhido.*

## <a name="development-environment-for-aspnet-core-apps"></a>Ambiente de desenvolvimento para aplicativos do ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Opções de ferramentas de desenvolvimento: IDE ou editor

Se você preferir um IDE avançado e completo ou um editor leve e ágeis, a Microsoft tem suas necessidades de desenvolvimento de aplicativos do ASP.NET Core.

**Visual Studio 2017.** Se você estiver usando *2017 do Visual Studio* podem criar ASP.NET Core aplicativos desde que você tenha o *desenvolvimento de plataforma cruzada do .NET Core* instalada da carga de trabalho. Figura 10-1 mostra a carga de trabalho necessária na caixa de diálogo de instalação 2017 do Visual Studio.

![](./media/image10-1.png)

**Figura 10-1.** Instalando a carga de trabalho do núcleo do .NET no Visual Studio de 2017.

[Baixe o Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**O Visual Studio Code e dotnet CLI** (ferramentas de plataforma cruzada para Mac, Linux e Windows). Se você preferir um editor leve e várias plataformas com suporte a qualquer linguagem de desenvolvimento, você pode usar o código do Microsoft Visual Studio e o dotnet CLI. Esses produtos fornecem uma experiência simple, porém robusta que simplifica o fluxo de trabalho do desenvolvedor. Além disso, o código do Visual Studio oferece suporte a extensões para C\# e desenvolvimento da web, fornecendo o intellisense e tarefas de atalho dentro do editor.

[Baixe o SDK do .NET Core](https://www.microsoft.com/net/download/core)

[Baixar o código do Visual Studio](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Fluxo de trabalho de desenvolvimento para aplicativos hospedados do Azure ASP.NET Core

O ciclo de vida de desenvolvimento de aplicativo começa em cada computador de um desenvolvedor, codificar o aplicativo usando o seu idioma preferencial e testá-lo localmente. Os desenvolvedores podem escolher seu sistema de controle de origem preferencial e podem configurar CI (integração contínua) e/ou entrega/implantação contínua (CD) usando um servidor de compilação ou com base em recursos internos do Azure.

Para começar a desenvolver um aplicativo ASP.NET Core usando CI/CD, você pode usar o Visual Studio Team Services ou sua organização possuir o Team Foundation Server (TFS).

### <a name="initial-setup"></a>Configuração inicial

Para criar um pipeline de versão para o seu aplicativo, você precisa ter o código do aplicativo no controle de origem. Configurar um repositório local e conectá-lo em um repositório remoto em um projeto de equipe. Siga estas instruções:

-   [Compartilhar seu código com o Visual Studio e o Git](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs) ou

-   [Compartilhe seu código com TFVC e o Visual Studio](https://docs.microsoft.com/vsts/tfvc/share-your-code-in-tfvc-vs)

Crie um serviço de aplicativo do Azure onde você implantará o aplicativo. Crie um aplicativo Web, vá para a folha de serviços de aplicativos no portal do Azure. Clique em + Adicionar, selecione o modelo de aplicativo Web, clique em criar e fornecer um nome e outros detalhes. O aplicativo web poderá ser acessado de {name}. azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Figura 10-2.** Criando um novo aplicativo de Web de serviço de aplicativo do Azure no Portal do Azure.

O processo de compilação de CI realizará uma compilação automatizada sempre que o novo código é confirmado para o repositório de controle de origem do projeto. Isso fornece um feedback imediato que cria o código (e, idealmente, passa testes automatizados) e potencialmente pode ser implantado. Esta compilação de CI produzirá uma web implantar artefato de pacote e publicá-lo para consumo pelo seu processo de CD.

[Definir o processo de compilação de CI](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#ci)

Certifique-se de habilitar a integração contínua para que o sistema irá enfileirar uma compilação sempre que alguém de sua equipe confirma o novo código. Testar a compilação e verificar se ele está produzindo um web implantar o pacote como um de seus artefatos.

Quando uma compilação for bem-sucedida, o processo de CD implantará os resultados de sua compilação de CI ao seu aplicativo web do Azure. Para configurar isso, você pode criar e configurar um *versão*, que será implantado para o serviço de aplicativo do Azure.

[Definir o processo de lançamento do CD](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#cd)

Depois que o pipeline de CI/CD estiver configurado, você pode simplesmente fazer atualizações em seu aplicativo web e confirmá-las ao controle de origem tê-los implantado.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Fluxo de trabalho para o desenvolvimento de aplicativos hospedados do Azure ASP.NET Core

Depois que você configurou sua conta do Azure e o processo de CI/CD, desenvolvimento de aplicativos hospedados do Azure ASP.NET Core é simple. A seguir estão as etapas básicas normalmente ao criar um aplicativo do ASP.NET Core, hospedado no serviço de aplicativo do Azure como um aplicativo Web, conforme ilustrado na Figura 10-3.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Figura 10-3.** Fluxo de trabalho passo a passo para criar aplicativos de ASP.NET Core e hospedá-los no Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Etapa 1. Loop interno do ambiente de desenvolvimento local

Desenvolvendo seu aplicativo ASP.NET Core para implantação no Azure não é diferente de desenvolvimento de seu aplicativo caso contrário. Use o ambiente de desenvolvimento local que você estiver familiarizado com, seja 2017 do Visual Studio ou o CLI dotnet e código do Visual Studio ou seu editor preferido. Você pode escrever código, executar e depurar suas alterações, executar testes automatizados e fazer confirmações locais ao controle de origem até que você está pronto para enviar por push as alterações ao seu repositório de controle de origem compartilhada.

#### <a name="step-2-application-code-repository"></a>Etapa 2. Repositório de código do aplicativo

Sempre que você está pronto para compartilhar seu código com sua equipe, você deve enviar por push as alterações do seu repositório local de origem para o repositório de origem compartilhada da sua equipe. Se você já trabalhou em uma ramificação personalizada, essa etapa geralmente envolve mesclar seu código em uma ramificação compartilhada (talvez por meio de um [solicitação pull](https://docs.microsoft.com/vsts/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Etapa 3. Servidor de compilação: A integração contínua. Pacote de compilação, teste,

Uma nova compilação é acionada no servidor de compilação sempre que uma nova confirmação é feita para o repositório de código de aplicativo compartilhado. Como parte do processo de CI, esta compilação totalmente deve compilar o aplicativo e executar testes automatizados para confirmar se que tudo está funcionando conforme o esperado. O resultado final do processo de CI deve ser uma versão de pacote do aplicativo web, pronto para a implantação.

#### <a name="step-4-build-server-continuous-delivery"></a>Etapa 4. Servidor de compilação: Fornecimento contínuo

Uma vez uma compilação como bem-sucedida, o processo de CD selecionará os artefatos de compilação produzidos. Isso incluirá uma web implantar o pacote. O servidor de compilação implantará esse pacote para o serviço de aplicativo do Azure, substituindo qualquer serviço existente com o recém-criado. Normalmente esta etapa tem como alvo um ambiente de preparo, mas alguns aplicativos implantar diretamente para a produção por meio de um processo do CD.

#### <a name="step-5-azure-app-service-web-app"></a>Etapa 5. Serviço de aplicativo do Azure. Aplicativo Web.

Uma vez implantado, o aplicativo do ASP.NET Core é executado dentro do contexto de um aplicativo de Web do serviço de aplicativo do Azure. Este aplicativo Web pode ser monitorado e configurado usando o Portal do Azure.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Etapa 6. Produção de monitoramento e diagnóstico

Durante a execução do aplicativo Web, você pode monitorar a integridade do aplicativo e coletar dados de comportamento do usuário e de diagnóstico. Application Insights está incluído no Visual Studio e oferece a instrumentação automática para aplicativos ASP.NET. Ele pode fornecer informações sobre uso, exceções, solicitações, desempenho e logs.

## <a name="references"></a>Referências

**Criar e implantar seu aplicativo ASP.NET Core para o Azure**  
<https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core>


>[!div class="step-by-step"]
[Previous] (test-asp-net-core-mvc-apps.md) [Next] (azure-hosting-recommendations-for-asp-net-web-apps.md)
