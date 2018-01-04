---
title: "Critérios de localização personalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b57a9535b34441a8f1c86beeffa94046cf8944f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-find-criteria"></a><span data-ttu-id="c8aea-102">Critérios de localização personalizados</span><span class="sxs-lookup"><span data-stu-id="c8aea-102">Custom Find Criteria</span></span>
<span data-ttu-id="c8aea-103">Este exemplo demonstra como criar uma correspondência de escopo personalizado usando a lógica e como implementar um serviço de descoberta personalizado.</span><span class="sxs-lookup"><span data-stu-id="c8aea-103">This sample demonstrates how to create a custom scope match using logic and how to implement a custom discovery service.</span></span> <span data-ttu-id="c8aea-104">Os clientes usam a funcionalidade de correspondência de escopo personalizado para refinar e tê ainda mais a funcionalidade de localização fornecida pelo sistema de descoberta do WCF.</span><span class="sxs-lookup"><span data-stu-id="c8aea-104">Clients use custom scope matching functionality to refine and further build on top of the system-provided find functionality of WCF Discovery.</span></span> <span data-ttu-id="c8aea-105">O cenário que abrange a este exemplo é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c8aea-105">The scenario this sample covers is as follows:</span></span>  
  
1.  <span data-ttu-id="c8aea-106">Um cliente está procurando por um serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="c8aea-106">A client is looking for a calculator service.</span></span>  
  
2.  <span data-ttu-id="c8aea-107">Para refinar sua pesquisa, o cliente deve usar um regra de correspondência de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="c8aea-107">To refine its search, the client must use a custom scope matching rule.</span></span>  
  
3.  <span data-ttu-id="c8aea-108">Acordo com esta regra, um serviço responde ao cliente se o seu ponto de extremidade corresponde a qualquer um dos escopos especificados pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="c8aea-108">According to this rule, a service responds back to the client if its endpoint matches any of the scopes specified by the client.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c8aea-109">Demonstra</span><span class="sxs-lookup"><span data-stu-id="c8aea-109">Demonstrates</span></span>  
  
-   <span data-ttu-id="c8aea-110">Criando um serviço de descoberta personalizado.</span><span class="sxs-lookup"><span data-stu-id="c8aea-110">Creating a custom discovery service.</span></span>  
  
-   <span data-ttu-id="c8aea-111">Implementando uma correspondência de escopo personalizado pelo algoritmo.</span><span class="sxs-lookup"><span data-stu-id="c8aea-111">Implementing a custom scope match by algorithm.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c8aea-112">Discussão</span><span class="sxs-lookup"><span data-stu-id="c8aea-112">Discussion</span></span>  
 <span data-ttu-id="c8aea-113">O cliente está procurando por tipo de "Ou" critérios de correspondência.</span><span class="sxs-lookup"><span data-stu-id="c8aea-113">The client is looking for "OR" type matching criteria.</span></span> <span data-ttu-id="c8aea-114">Um serviço responde novamente se os escopos em seus pontos de extremidade correspondem a nenhum dos escopos fornecidos pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="c8aea-114">A service responds back if the scopes on its endpoints match any of the scopes provided by the client.</span></span> <span data-ttu-id="c8aea-115">Nesse caso, o cliente está procurando por um serviço de cálculo que tenha qualquer um dos escopos da lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="c8aea-115">In this case, the client is looking for a calculator service that has any of the scopes in the following list:</span></span>  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 <span data-ttu-id="c8aea-116">Para fazer isso, o cliente direciona os serviços para usar um regra de correspondência, passando uma correspondência de escopo personalizado pelo URI de escopo personalizado.</span><span class="sxs-lookup"><span data-stu-id="c8aea-116">To accomplish this, the client directs services to use a custom scope matching rule by passing in a custom scope match by URI.</span></span> <span data-ttu-id="c8aea-117">Para facilitar a correspondência de escopo personalizado, o serviço deve usar um serviço de detecção personalizada que compreende a regra de correspondência de escopo personalizado e implementa a lógica de correspondência associada.</span><span class="sxs-lookup"><span data-stu-id="c8aea-117">To facilitate the custom scope matching, the service must use a custom discovery service that understands the custom scope match rule and implements the associated matching logic.</span></span>  
  
 <span data-ttu-id="c8aea-118">No projeto do cliente, abra o arquivo Program.cs.</span><span class="sxs-lookup"><span data-stu-id="c8aea-118">In the client project, open the Program.cs file.</span></span> <span data-ttu-id="c8aea-119">Observe que o `ScopeMatchBy` campo o `FindCriteria` objeto é definido como um URI específico.</span><span class="sxs-lookup"><span data-stu-id="c8aea-119">Note that the `ScopeMatchBy` field of the `FindCriteria` object is set to a specific URI.</span></span> <span data-ttu-id="c8aea-120">Esse identificador é enviado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="c8aea-120">This identifier is sent to the service.</span></span> <span data-ttu-id="c8aea-121">Se o serviço não entender a essa regra, ele ignora a solicitação do cliente localizar.</span><span class="sxs-lookup"><span data-stu-id="c8aea-121">If the service does not understand this rule, it ignores the client’s find request.</span></span>  
  
 <span data-ttu-id="c8aea-122">Abra o projeto de serviço.</span><span class="sxs-lookup"><span data-stu-id="c8aea-122">Open the service project.</span></span> <span data-ttu-id="c8aea-123">Três arquivos são usados para implementar o serviço de detecção personalizada:</span><span class="sxs-lookup"><span data-stu-id="c8aea-123">Three files are used to implement the Custom Discovery Service:</span></span>  
  
1.  <span data-ttu-id="c8aea-124">**AsyncResult.cs**: esta é a implementação do `AsyncResult` que é exigido pelos métodos de descoberta.</span><span class="sxs-lookup"><span data-stu-id="c8aea-124">**AsyncResult.cs**: This is the implementation of the `AsyncResult` that is required by Discovery methods.</span></span>  
  
2.  <span data-ttu-id="c8aea-125">**CustomDiscoveryService.cs**: este arquivo implementa o serviço de descoberta personalizado.</span><span class="sxs-lookup"><span data-stu-id="c8aea-125">**CustomDiscoveryService.cs**: This file implements the custom discovery service.</span></span> <span data-ttu-id="c8aea-126">A implementação estende o <xref:System.ServiceModel.Discovery.DiscoveryService> classe e substitui os métodos necessários.</span><span class="sxs-lookup"><span data-stu-id="c8aea-126">The implementation extends the <xref:System.ServiceModel.Discovery.DiscoveryService> class and overrides the necessary methods.</span></span> <span data-ttu-id="c8aea-127">Observe a implementação de <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c8aea-127">Note the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> method.</span></span> <span data-ttu-id="c8aea-128">O método verifica se a correspondência de escopo personalizado pela regra foi especificada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="c8aea-128">The method checks to see whether the custom scope match by rule was specified by the client.</span></span> <span data-ttu-id="c8aea-129">Este é o mesmo URI personalizado que o cliente especificado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c8aea-129">This is the same custom URI that the client specified previously.</span></span> <span data-ttu-id="c8aea-130">Se a regra personalizada for especificada, o caminho do código que implementa a lógica de correspondência de "OR" é seguido.</span><span class="sxs-lookup"><span data-stu-id="c8aea-130">If the custom rule is specified, the code path that implements the "OR" match logic is followed.</span></span>  
  
     <span data-ttu-id="c8aea-131">Essa lógica personalizada passa por todos os escopos em cada um dos pontos de extremidade que tem o serviço.</span><span class="sxs-lookup"><span data-stu-id="c8aea-131">This custom logic goes through all of the scopes on each of the endpoints that the service has.</span></span> <span data-ttu-id="c8aea-132">Se qualquer um dos escopos do ponto de extremidade corresponder a qualquer um dos escopos fornecidos pelo cliente, o serviço de descoberta adiciona o ponto de extremidade para a resposta que é enviada de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="c8aea-132">If any of the endpoint's scopes match any of the scopes provided by the client, the discovery service adds that endpoint to the response that is sent back to the client.</span></span>  
  
3.  <span data-ttu-id="c8aea-133">**CustomDiscoveryExtension.cs**: é a última etapa na implementação do serviço de descoberta para se conectar a esta implementação personalizado descobrir o serviço para o host de serviço.</span><span class="sxs-lookup"><span data-stu-id="c8aea-133">**CustomDiscoveryExtension.cs**: The last step in implementing the discovery service is to connect this implementation of the custom discover service to the service host.</span></span> <span data-ttu-id="c8aea-134">A classe auxiliar usada aqui é o `CustomDiscoveryExtension` classe.</span><span class="sxs-lookup"><span data-stu-id="c8aea-134">The helper class used here is the `CustomDiscoveryExtension` class.</span></span> <span data-ttu-id="c8aea-135">Essa classe estende a <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="c8aea-135">This class extends the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> class.</span></span> <span data-ttu-id="c8aea-136">O usuário deve substituir o <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c8aea-136">The user must override the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> method.</span></span> <span data-ttu-id="c8aea-137">Nesse caso, o método retorna uma instância do serviço de descoberta personalizado que foi criado antes.</span><span class="sxs-lookup"><span data-stu-id="c8aea-137">In this case, the method returns an instance of the custom discovery service that was created before.</span></span> <span data-ttu-id="c8aea-138">`PublishedEndpoints`é um <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> que contém todos os pontos de extremidade de aplicativo que são adicionados para o <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c8aea-138">`PublishedEndpoints` is a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> that contains all of the application endpoints that are added to the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="c8aea-139">O serviço de descoberta personalizado usa isso para preencher sua lista interna.</span><span class="sxs-lookup"><span data-stu-id="c8aea-139">The custom discovery service uses this to populate its internal list.</span></span> <span data-ttu-id="c8aea-140">Um usuário pode para adicionar outros metadados do ponto de extremidade também.</span><span class="sxs-lookup"><span data-stu-id="c8aea-140">A user can to add other endpoint metadata as well.</span></span>  
  
 <span data-ttu-id="c8aea-141">Por fim, abra Program.cs.</span><span class="sxs-lookup"><span data-stu-id="c8aea-141">Lastly, open Program.cs.</span></span> <span data-ttu-id="c8aea-142">Observe que tanto o <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> e `CustomDiscoveryExtension` são adicionados ao host.</span><span class="sxs-lookup"><span data-stu-id="c8aea-142">Note that both the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and `CustomDiscoveryExtension` are added to the host.</span></span> <span data-ttu-id="c8aea-143">Quando isso é feito e o host tem um ponto de extremidade através da qual receber mensagens de descoberta, o aplicativo pode usar o serviço de descoberta personalizado.</span><span class="sxs-lookup"><span data-stu-id="c8aea-143">Once this is done and the host has an endpoint over which to receive discovery messages, the application can use the custom discovery service.</span></span>  
  
 <span data-ttu-id="c8aea-144">Observe que o cliente é capaz de encontrar o serviço sem saber o endereço.</span><span class="sxs-lookup"><span data-stu-id="c8aea-144">Observe that the client is able to find the service without knowing its address.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8aea-145">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c8aea-145">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c8aea-146">Abra a solução que contém o projeto.</span><span class="sxs-lookup"><span data-stu-id="c8aea-146">Open the solution that contains the project.</span></span>  
  
2.  <span data-ttu-id="c8aea-147">Compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="c8aea-147">Build the project.</span></span>  
  
3.  <span data-ttu-id="c8aea-148">Execute o aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="c8aea-148">Run the service application.</span></span>  
  
4.  <span data-ttu-id="c8aea-149">Execute o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="c8aea-149">Run the client application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8aea-150">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c8aea-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8aea-151">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c8aea-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c8aea-152">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c8aea-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8aea-153">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c8aea-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
