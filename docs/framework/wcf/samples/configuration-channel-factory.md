---
title: Factory do canal de configuração
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1f95356b0b473b297b36c7661c849589e9c0d6ef
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483730"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="c15b2-102">Factory do canal de configuração</span><span class="sxs-lookup"><span data-stu-id="c15b2-102">Configuration Channel Factory</span></span>
<span data-ttu-id="c15b2-103">Este exemplo aborda o uso do <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="c15b2-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="c15b2-104">O <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permite o gerenciamento centralizado de configuração de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="c15b2-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="c15b2-105">Isso também pode ser útil em cenários em que a configuração é selecionada ou alterada depois que o tempo de carregamento de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c15b2-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c15b2-106">Demonstra</span><span class="sxs-lookup"><span data-stu-id="c15b2-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="c15b2-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="c15b2-107">Discussion</span></span>  
 <span data-ttu-id="c15b2-108">Este exemplo mostra como usar <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> para adicionar um arquivo de configuração específico para um aplicativo cliente, sem a necessidade de usar o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="c15b2-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="c15b2-109">O exemplo consiste em dois projetos.</span><span class="sxs-lookup"><span data-stu-id="c15b2-109">The sample consists of two projects.</span></span> <span data-ttu-id="c15b2-110">O primeiro projeto é um serviço simples que é executado para responder a mensagens recebidas dos clientes.</span><span class="sxs-lookup"><span data-stu-id="c15b2-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="c15b2-111">O segundo projeto é um aplicativo cliente que cria dois <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objetos usando um <xref:System.Configuration.ExeConfigurationFileMap> Test.config arquivo de configuração e os utiliza para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="c15b2-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="c15b2-112">Ambos os clientes se comunicam com o serviço usando a configuração especificada em Test.config.</span><span class="sxs-lookup"><span data-stu-id="c15b2-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="c15b2-113">O código a seguir adiciona um arquivo de configuração personalizada a um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="c15b2-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c15b2-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c15b2-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c15b2-115">Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="c15b2-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="c15b2-116">A solução ConfigurationChannelFactory (2 projetos) com o botão direito e, em seguida, selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c15b2-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="c15b2-117">Na **propriedades comuns**, selecione **projeto de inicialização**e, em seguida, clique em **vários projetos de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="c15b2-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="c15b2-118">Mover o **Service** do projeto para o início da lista, com o **ação 'Start'** e, em seguida, mova o **cliente** projeto depois do **serviço**projeto, também com o **a ação 'Start'**, portanto, o **cliente** projeto é executado após o **serviço** projeto.</span><span class="sxs-lookup"><span data-stu-id="c15b2-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="c15b2-119">Clique em **Okey**, em seguida, pressione F5 (ou CTRL + F5) para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="c15b2-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c15b2-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c15b2-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c15b2-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c15b2-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c15b2-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c15b2-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c15b2-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c15b2-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
