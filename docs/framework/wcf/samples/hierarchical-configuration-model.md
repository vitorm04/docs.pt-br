---
title: Modelo de configuração hierárquica
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 233a8d4ba36835ab26e0c4a8cd044cf60d497a0b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806624"
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="81a0c-102">Modelo de configuração hierárquica</span><span class="sxs-lookup"><span data-stu-id="81a0c-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="81a0c-103">Este exemplo demonstra como implementar uma hierarquia de arquivos de configuração para serviços.</span><span class="sxs-lookup"><span data-stu-id="81a0c-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="81a0c-104">Ele também mostra como as associações, comportamentos de serviço e comportamentos de ponto de extremidade são herdados de níveis mais altos na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="81a0c-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="81a0c-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="81a0c-105">Sample details</span></span>  
 <span data-ttu-id="81a0c-106">Um dos recursos desenvolvidos para o WCF no [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] é o aperfeiçoamento no modelo de configuração hierárquica.</span><span class="sxs-lookup"><span data-stu-id="81a0c-106">One of the features developed for WCF in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="81a0c-107">Um exemplo de um modelo de configuração hierárquica seria definida por Machine. config -> Rootweb.config -> Web. config. Em [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], essas associações e comportamentos que são definidos em níveis superiores na hierarquia de configuração são adicionados aos serviços sem nenhuma configuração explícita.</span><span class="sxs-lookup"><span data-stu-id="81a0c-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="81a0c-108">Este exemplo mostra como é possível simplificar sua configuração de serviço confiando em elementos de configuração definidos no computador ou no nível do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81a0c-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="81a0c-109">Este exemplo consiste em nove serviços, definidos em três níveis de hierarquia.</span><span class="sxs-lookup"><span data-stu-id="81a0c-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="81a0c-110">`Service1` está na raiz.</span><span class="sxs-lookup"><span data-stu-id="81a0c-110">`Service1` is at the root.</span></span> <span data-ttu-id="81a0c-111">`Service2` e `Service3` herdam os elementos de padrão de `Service1`.</span><span class="sxs-lookup"><span data-stu-id="81a0c-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="81a0c-112">`Service4`, `Service5`, `Service6` e `Service7` são definidos em um terceiro nível da hierarquia de herança os elementos de padrão de `Service3`.</span><span class="sxs-lookup"><span data-stu-id="81a0c-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="81a0c-113">Por fim `Service10` e `Service11` estão em um quarto nível da hierarquia.</span><span class="sxs-lookup"><span data-stu-id="81a0c-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="81a0c-114">Todos os serviços de implementam o `IDesc` contrato.</span><span class="sxs-lookup"><span data-stu-id="81a0c-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="81a0c-115">A seguir está a definição do `IDesc` interface que mostra os métodos expostos nessa interface.</span><span class="sxs-lookup"><span data-stu-id="81a0c-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="81a0c-116">O `IDesc` interface é definida em Service1.</span><span class="sxs-lookup"><span data-stu-id="81a0c-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
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
  
 <span data-ttu-id="81a0c-117">A implementação desses métodos pelos serviços é simples.</span><span class="sxs-lookup"><span data-stu-id="81a0c-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="81a0c-118">`ListEndpoints` itera em todos os pontos de extremidade do serviço e retorna uma lista de todos os pontos de extremidade que tem o serviço.</span><span class="sxs-lookup"><span data-stu-id="81a0c-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="81a0c-119">`ListServiceBehaviors` itera em todos os comportamentos adicionados ao serviço e retorna a lista de todos os comportamentos de serviço associado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="81a0c-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="81a0c-120">`ListEndpointBehaviors` se comporta de forma semelhante ao `ListServiceBehaviors`, mas retorna a lista de comportamentos de ponto de extremidade em vez disso.</span><span class="sxs-lookup"><span data-stu-id="81a0c-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="81a0c-121">Essa implementação permite que o cliente para saber quantos pontos de extremidade de serviço está expondo e quais comportamentos de serviço e comportamentos de ponto de extremidade foram adicionados ao serviço.</span><span class="sxs-lookup"><span data-stu-id="81a0c-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="81a0c-122">O cliente tiver sido implementado como parte do exemplo adiciona uma referência de serviço para todos os serviços na solução e mostra esses elementos para cada um dos serviços.</span><span class="sxs-lookup"><span data-stu-id="81a0c-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="81a0c-123">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="81a0c-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="81a0c-124">Para executar o cliente</span><span class="sxs-lookup"><span data-stu-id="81a0c-124">To run the client</span></span>  
  
1.  <span data-ttu-id="81a0c-125">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo ConfigHierarchicalModel.sln.</span><span class="sxs-lookup"><span data-stu-id="81a0c-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="81a0c-126">O projeto de cliente não já está definido como o projeto de inicialização, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="81a0c-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="81a0c-127">Em **Solution Explorer**, a solução e, em seguida, selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="81a0c-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="81a0c-128">Em **propriedades comuns**, selecione **projeto de inicialização**e, em seguida, clique em **único projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="81a0c-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="81a0c-129">Do **único projeto de inicialização** lista suspensa, selecione **cliente**.</span><span class="sxs-lookup"><span data-stu-id="81a0c-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="81a0c-130">Clique em **Okey** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="81a0c-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="81a0c-131">Para criar o exemplo, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="81a0c-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="81a0c-132">Para executar o cliente, pressione Ctrl + F5.</span><span class="sxs-lookup"><span data-stu-id="81a0c-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81a0c-133">Se essas etapas não funcionar, certifique-se de que seu ambiente foi adequadamente configurado, usando as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="81a0c-133">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="81a0c-134">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81a0c-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="81a0c-135">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81a0c-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="81a0c-136">Para executar o exemplo em uma única ou várias configurações de computador, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="81a0c-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81a0c-137">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="81a0c-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="81a0c-138">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="81a0c-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81a0c-139">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="81a0c-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81a0c-140">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="81a0c-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="81a0c-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81a0c-141">See Also</span></span>  
 [<span data-ttu-id="81a0c-142">Exemplos de gerenciamento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="81a0c-142">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)
