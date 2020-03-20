---
title: Factory do canal de configuração
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183945"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="b24da-102">Factory do canal de configuração</span><span class="sxs-lookup"><span data-stu-id="b24da-102">Configuration Channel Factory</span></span>
<span data-ttu-id="b24da-103">Esta amostra abrange o <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>uso do .</span><span class="sxs-lookup"><span data-stu-id="b24da-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="b24da-104">O <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permite o gerenciamento central da configuração do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="b24da-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="b24da-105">Isso também pode ser útil em cenários nos quais a configuração é selecionada ou alterada após o tempo de carregamento do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b24da-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b24da-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="b24da-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="b24da-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="b24da-107">Discussion</span></span>
 <span data-ttu-id="b24da-108">Esta amostra mostra <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> como usar para adicionar um arquivo de configuração específico a um aplicativo cliente, sem ter que usar o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="b24da-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="b24da-109">A amostra consiste em dois projetos.</span><span class="sxs-lookup"><span data-stu-id="b24da-109">The sample consists of two projects.</span></span> <span data-ttu-id="b24da-110">O primeiro projeto é um serviço simples que funciona para responder às mensagens vindas dos clientes.</span><span class="sxs-lookup"><span data-stu-id="b24da-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="b24da-111">O segundo projeto é um aplicativo <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> cliente <xref:System.Configuration.ExeConfigurationFileMap> que constrói dois objetos usando um para o arquivo de configuração Test.config e os usa para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="b24da-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="b24da-112">Ambos os clientes se comunicam com o serviço usando a configuração especificada em Test.config.</span><span class="sxs-lookup"><span data-stu-id="b24da-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="b24da-113">O código a seguir adiciona um arquivo de configuração personalizado a um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="b24da-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b24da-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="b24da-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b24da-115">Abra o Visual Studio 2012 com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="b24da-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="b24da-116">Clique com o botão direito do mouse na solução ConfigurationChannelFactory (2 projetos) e, em seguida, selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b24da-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="b24da-117">Em **Propriedades Comuns,** selecione **Projeto de Inicialização**e clique em **Vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="b24da-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="b24da-118">Mova o projeto **Serviço** para o início da lista, com a **Ação 'Iniciar'** e, em seguida, mova o projeto **Cliente** após o projeto **Serviço,** também com a **Ação 'Start',** para que o projeto **Cliente** seja executado após o projeto **Serviço.**</span><span class="sxs-lookup"><span data-stu-id="b24da-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="b24da-119">Clique **em OK**e pressione F5 (ou CTRL+F5) para executar a amostra.</span><span class="sxs-lookup"><span data-stu-id="b24da-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b24da-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b24da-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b24da-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b24da-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b24da-122">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="b24da-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b24da-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b24da-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
