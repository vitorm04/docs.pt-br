---
title: Tratamento de erros do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26dfea83400b5d601fabc5cfb52bc71a4d5e4f6f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-error-handling"></a><span data-ttu-id="15a75-102">Tratamento de erros do WCF</span><span class="sxs-lookup"><span data-stu-id="15a75-102">WCF Error Handling</span></span>
<span data-ttu-id="15a75-103">Os erros encontrados por um aplicativo WCF pertencem a um dos três grupos:</span><span class="sxs-lookup"><span data-stu-id="15a75-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1.  <span data-ttu-id="15a75-104">Erros de comunicação</span><span class="sxs-lookup"><span data-stu-id="15a75-104">Communication Errors</span></span>  
  
2.  <span data-ttu-id="15a75-105">Erros de canal/proxy</span><span class="sxs-lookup"><span data-stu-id="15a75-105">Proxy/Channel Errors</span></span>  
  
3.  <span data-ttu-id="15a75-106">Erros de aplicativo</span><span class="sxs-lookup"><span data-stu-id="15a75-106">Application Errors</span></span>  
  
 <span data-ttu-id="15a75-107">Erros de comunicação ocorrem quando uma rede não estiver disponível, um cliente usa um endereço incorreto ou o host de serviço não está escutando para mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="15a75-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="15a75-108">Os erros desse tipo são retornados ao cliente como <xref:System.ServiceModel.CommunicationException> ou <xref:System.ServiceModel.CommunicationException>-classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="15a75-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="15a75-109">Erros de canal/proxy são erros que ocorrem dentro do canal ou o próprio proxy.</span><span class="sxs-lookup"><span data-stu-id="15a75-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="15a75-110">Os erros desse tipo incluem: tentativa de usar um proxy ou canal que foi fechado, existe uma incompatibilidade de contrato entre o cliente e o serviço ou as credenciais do cliente são rejeitadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="15a75-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="15a75-111">Há muitos tipos diferentes de erros nesta categoria, muitos para listar aqui.</span><span class="sxs-lookup"><span data-stu-id="15a75-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="15a75-112">Os erros desse tipo são retornados ao cliente como-é (Nenhuma transformação é executada nos objetos de exceção).</span><span class="sxs-lookup"><span data-stu-id="15a75-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="15a75-113">Erros de aplicativo ocorrem durante a execução de uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="15a75-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="15a75-114">Os erros desse tipo são enviados ao cliente como <xref:System.ServiceModel.FaultException> ou <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="15a75-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="15a75-115">Tratamento de erros em WCF é executado por um ou mais dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="15a75-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
-   <span data-ttu-id="15a75-116">Manipulando diretamente a exceção é gerada.</span><span class="sxs-lookup"><span data-stu-id="15a75-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="15a75-117">Isso é feito apenas para comunicação e erros de canal/proxy.</span><span class="sxs-lookup"><span data-stu-id="15a75-117">This is only done for communication and proxy/channel errors.</span></span>  
  
-   <span data-ttu-id="15a75-118">Usando contratos de falha</span><span class="sxs-lookup"><span data-stu-id="15a75-118">Using fault contracts</span></span>  
  
-   <span data-ttu-id="15a75-119">Implementando o <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span><span class="sxs-lookup"><span data-stu-id="15a75-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
-   <span data-ttu-id="15a75-120">Tratamento <xref:System.ServiceModel.ServiceHost> eventos</span><span class="sxs-lookup"><span data-stu-id="15a75-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="15a75-121">Contratos de falha</span><span class="sxs-lookup"><span data-stu-id="15a75-121">Fault Contracts</span></span>  
 <span data-ttu-id="15a75-122">Contratos de falha permitem que você defina os erros que podem ocorrer durante a operação de serviço em uma plataforma de maneira independente.</span><span class="sxs-lookup"><span data-stu-id="15a75-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="15a75-123">Por padrão, todas as exceções lançadas a partir de uma operação de serviço serão retornadas ao cliente como um <xref:System.ServiceModel.FaultException> objeto.</span><span class="sxs-lookup"><span data-stu-id="15a75-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="15a75-124">O <xref:System.ServiceModel.FaultException> objeto conterá informações muito pouco.</span><span class="sxs-lookup"><span data-stu-id="15a75-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="15a75-125">Você pode controlar as informações enviadas para o cliente definir um contrato de falha e retornando o erro como uma <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="15a75-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="15a75-126">[Especificando e lidando com falhas em contratos e serviços](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="15a75-126"> [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="15a75-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="15a75-127">IErrorHandler</span></span>  
 <span data-ttu-id="15a75-128">O <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface permite a você mais controle sobre como seu aplicativo WCF responde a erros.</span><span class="sxs-lookup"><span data-stu-id="15a75-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="15a75-129">Isso lhe dá controle total sobre a mensagem de falha é retornada ao cliente e permite que você execute o processamento, como o log de erro personalizada.</span><span class="sxs-lookup"><span data-stu-id="15a75-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<span data-ttu-id="15a75-130"><xref:System.ServiceModel.Dispatcher.IErrorHandler> e [controle estendido através de tratamento de erros e emissão de relatórios](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="15a75-130"> <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="15a75-131">Eventos do ServiceHost</span><span class="sxs-lookup"><span data-stu-id="15a75-131">ServiceHost Events</span></span>  
 <span data-ttu-id="15a75-132">O <xref:System.ServiceModel.ServiceHost> classe hospeda serviços e define vários eventos que podem ser necessárias para tratamento de erros.</span><span class="sxs-lookup"><span data-stu-id="15a75-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="15a75-133">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="15a75-133">For example:</span></span>  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="15a75-134"> <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="15a75-134"> <xref:System.ServiceModel.ServiceHost></span></span>
