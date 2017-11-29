---
title: "Modelo de configuração hierárquica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b3b170e3e6453c14f557786572c54ac6f67c3db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="75b89-102">Modelo de configuração hierárquica</span><span class="sxs-lookup"><span data-stu-id="75b89-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="75b89-103">Este exemplo demonstra como implementar uma hierarquia de arquivos de configuração para serviços.</span><span class="sxs-lookup"><span data-stu-id="75b89-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="75b89-104">Ele também mostra como as associações, comportamentos de serviço e comportamentos de ponto de extremidade são herdados de níveis mais altos na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="75b89-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="75b89-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="75b89-105">Sample details</span></span>  
 <span data-ttu-id="75b89-106">Um dos recursos desenvolvidos para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] é o aperfeiçoamento no modelo de configuração hierárquica.</span><span class="sxs-lookup"><span data-stu-id="75b89-106">One of the features developed for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="75b89-107">Um exemplo de um modelo de configuração hierárquica seria definida por Machine. config -> Rootweb.config -> Web. config. Em [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], essas associações e comportamentos que são definidos em níveis superiores na hierarquia de configuração são adicionados aos serviços sem nenhuma configuração explícita.</span><span class="sxs-lookup"><span data-stu-id="75b89-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="75b89-108">Este exemplo mostra como é possível simplificar sua configuração de serviço confiando em elementos de configuração definidos no computador ou no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="75b89-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="75b89-109">Este exemplo consiste em nove serviços, definidos em três níveis de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="75b89-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="75b89-110">`Service1`está na raiz.</span><span class="sxs-lookup"><span data-stu-id="75b89-110">`Service1` is at the root.</span></span> <span data-ttu-id="75b89-111">`Service2`e `Service3` herdam os elementos de padrão de `Service1`.</span><span class="sxs-lookup"><span data-stu-id="75b89-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="75b89-112">`Service4`, `Service5`, `Service6` e `Service7` são definidos em um terceiro nível da hierarquia de herança os elementos de padrão de `Service3`.</span><span class="sxs-lookup"><span data-stu-id="75b89-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="75b89-113">Por fim `Service10` e `Service11` estão em um quarto nível da hierarquia.</span><span class="sxs-lookup"><span data-stu-id="75b89-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="75b89-114">Todos os serviços de implementam o `IDesc` contrato.</span><span class="sxs-lookup"><span data-stu-id="75b89-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="75b89-115">A seguir está a definição do `IDesc` interface que mostra os métodos expostos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="75b89-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="75b89-116">O `IDesc` interface é definida em Service1.</span><span class="sxs-lookup"><span data-stu-id="75b89-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 <span data-ttu-id="75b89-117">A implementação desses métodos pelos serviços é simples.</span><span class="sxs-lookup"><span data-stu-id="75b89-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="75b89-118">`ListEndpoints`itera em todos os pontos de extremidade do serviço e retorna uma lista de todos os pontos de extremidade que tem o serviço.</span><span class="sxs-lookup"><span data-stu-id="75b89-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="75b89-119">`ListServiceBehaviors`itera em todos os comportamentos adicionados ao serviço e retorna a lista de todos os comportamentos de serviço associado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="75b89-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="75b89-120">`ListEndpointBehaviors`se comporta de forma semelhante ao `ListServiceBehaviors`, mas retorna a lista de comportamentos de ponto de extremidade em vez disso.</span><span class="sxs-lookup"><span data-stu-id="75b89-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="75b89-121">Essa implementação permite que o cliente para saber quantos pontos de extremidade de serviço está expondo e quais comportamentos de serviço e comportamentos de ponto de extremidade foram adicionados ao serviço.</span><span class="sxs-lookup"><span data-stu-id="75b89-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="75b89-122">O cliente tiver sido implementado como parte do exemplo adiciona uma referência de serviço para todos os serviços na solução e mostra esses elementos para cada um dos serviços.</span><span class="sxs-lookup"><span data-stu-id="75b89-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="75b89-123">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="75b89-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="75b89-124">Para executar o cliente</span><span class="sxs-lookup"><span data-stu-id="75b89-124">To run the client</span></span>  
  
1.  <span data-ttu-id="75b89-125">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo ConfigHierarchicalModel.sln.</span><span class="sxs-lookup"><span data-stu-id="75b89-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="75b89-126">O projeto de cliente não já está definido como o projeto de inicialização, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="75b89-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="75b89-127">Em **Solution Explorer**, a solução e, em seguida, selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="75b89-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="75b89-128">Em **propriedades comuns**, selecione **projeto de inicialização**e, em seguida, clique em **único projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="75b89-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="75b89-129">Do **único projeto de inicialização** lista suspensa, selecione **cliente**.</span><span class="sxs-lookup"><span data-stu-id="75b89-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="75b89-130">Clique em **Okey** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="75b89-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="75b89-131">Para criar o exemplo, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="75b89-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="75b89-132">Para executar o cliente, pressione Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="75b89-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75b89-133">Se essas etapas não funcionar, certifique-se de que seu ambiente foi adequadamente configurado, usando as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="75b89-133">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="75b89-134">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75b89-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="75b89-135">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75b89-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="75b89-136">Para executar o exemplo em uma única ou várias configurações de computador, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="75b89-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75b89-137">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="75b89-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="75b89-138">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="75b89-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="75b89-139">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="75b89-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="75b89-140">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="75b89-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="75b89-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75b89-141">See Also</span></span>  
 [<span data-ttu-id="75b89-142">Exemplos de gerenciamento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="75b89-142">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)
