---
title: "Factory do canal de configuração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13001ff291c1d2874e5c9ce6e427afe09067432a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="e93e3-102">Factory do canal de configuração</span><span class="sxs-lookup"><span data-stu-id="e93e3-102">Configuration Channel Factory</span></span>
<span data-ttu-id="e93e3-103">Ele aborda o uso do <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="e93e3-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="e93e3-104">O <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permite o gerenciamento centralizado de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="e93e3-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client configuration.</span></span> <span data-ttu-id="e93e3-105">Isso também pode ser útil em cenários em que a configuração é selecionada ou alterada depois que o domínio de aplicativo de tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="e93e3-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e93e3-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="e93e3-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="e93e3-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="e93e3-107">Discussion</span></span>  
 <span data-ttu-id="e93e3-108">Este exemplo mostra como usar <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> para adicionar um arquivo de configuração específico a um aplicativo cliente, sem a necessidade de usar o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="e93e3-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="e93e3-109">O exemplo consiste em dois projetos.</span><span class="sxs-lookup"><span data-stu-id="e93e3-109">The sample consists of two projects.</span></span> <span data-ttu-id="e93e3-110">O primeiro projeto é um serviço simple que é executado para responder a mensagens recebidas dos clientes.</span><span class="sxs-lookup"><span data-stu-id="e93e3-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="e93e3-111">O segundo projeto é um aplicativo cliente que cria dois <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objetos usando um <xref:System.Configuration.ExeConfigurationFileMap> Test.config arquivo de configuração e as usa para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="e93e3-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="e93e3-112">Ambos os clientes se comunicam com o serviço usando a configuração especificada em Test.config.</span><span class="sxs-lookup"><span data-stu-id="e93e3-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="e93e3-113">O código a seguir adiciona um arquivo de configuração personalizada para um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="e93e3-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e93e3-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e93e3-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e93e3-115">Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="e93e3-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="e93e3-116">A solução ConfigurationChannelFactory (2 projetos) e, em seguida, selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e93e3-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="e93e3-117">Em **propriedades comuns**, selecione **projeto de inicialização**e, em seguida, clique em **vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="e93e3-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="e93e3-118">Mover o **Service** de projeto para o início da lista, com o **ação 'Start'**e, em seguida, mova o **cliente** projeto após o **serviço**projeto, também com o **ação 'Start'**, portanto, o **cliente** projeto é executado após o **Service** projeto.</span><span class="sxs-lookup"><span data-stu-id="e93e3-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="e93e3-119">Clique em **Okey**e, em seguida, pressione F5 (ou CTRL + F5) para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="e93e3-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e93e3-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e93e3-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e93e3-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e93e3-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e93e3-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e93e3-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e93e3-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e93e3-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
