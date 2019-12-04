---
title: Factory do canal de configuração
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1a236f1812d3124e83702a97e1877b7fec10be64
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715497"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="8f3bb-102">Factory do canal de configuração</span><span class="sxs-lookup"><span data-stu-id="8f3bb-102">Configuration Channel Factory</span></span>
<span data-ttu-id="8f3bb-103">Este exemplo cobre o uso do <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="8f3bb-104">O <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permite o gerenciamento central da configuração do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="8f3bb-105">Isso também pode ser útil em cenários em que a configuração é selecionada ou alterada após o tempo de carregamento do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8f3bb-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="8f3bb-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="8f3bb-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="8f3bb-107">Discussion</span></span>
 <span data-ttu-id="8f3bb-108">Este exemplo mostra como usar <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> para adicionar um arquivo de configuração específico a um aplicativo cliente, sem precisar usar o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="8f3bb-109">O exemplo consiste em dois projetos.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-109">The sample consists of two projects.</span></span> <span data-ttu-id="8f3bb-110">O primeiro projeto é um serviço simples que é executado para responder às mensagens provenientes dos clientes.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="8f3bb-111">O segundo projeto é um aplicativo cliente que cria dois objetos <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> usando um <xref:System.Configuration.ExeConfigurationFileMap> para o arquivo de configuração Test. config e os usa para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="8f3bb-112">Ambos os clientes se comunicam com o serviço usando a configuração especificada em Test. config.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="8f3bb-113">O código a seguir adiciona um arquivo de configuração personalizado a um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8f3bb-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="8f3bb-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8f3bb-115">Abra o Visual Studio 2012 com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="8f3bb-116">Clique com o botão direito do mouse na solução ConfigurationChannelFactory (2 projetos) e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="8f3bb-117">Em **Propriedades comuns**, selecione **projeto de inicialização**e clique em **vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="8f3bb-118">Mova o projeto de **serviço** para o início da lista, com a **ação ' Iniciar '** e, em seguida, mova o projeto **cliente** após o projeto de **serviço** , também com a **ação ' Iniciar '** , para que o projeto **cliente** seja executado após o projeto de **serviço** .</span><span class="sxs-lookup"><span data-stu-id="8f3bb-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="8f3bb-119">Clique em **OK**e pressione F5 (ou CTRL + F5) para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f3bb-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8f3bb-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8f3bb-122">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f3bb-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="8f3bb-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
