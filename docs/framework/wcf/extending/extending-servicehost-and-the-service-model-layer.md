---
title: "Estendendo a camada de modelo de serviço e o ServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67ed4be3211af141af87da2406e81ff5e2fbb767
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="56c64-102">Estendendo a camada de modelo de serviço e o ServiceHost</span><span class="sxs-lookup"><span data-stu-id="56c64-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="56c64-103">A camada de modelo de serviço é responsável por recebendo mensagens de entrada fora dos canais subjacentes, convertendo-os em invocações do método no código do aplicativo e enviar os resultados de volta para o chamador.</span><span class="sxs-lookup"><span data-stu-id="56c64-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="56c64-104">Extensões do modelo de serviço modificam ou implementam a execução ou o comportamento de comunicação e recursos que envolvem a funcionalidade de cliente ou o distribuidor, comportamentos personalizados, mensagem e interceptação de parâmetro e outras funcionalidades de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="56c64-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="56c64-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="56c64-105">In This Section</span></span>  
 [<span data-ttu-id="56c64-106">Estendendo clientes</span><span class="sxs-lookup"><span data-stu-id="56c64-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="56c64-107">Descreve as interfaces que podem interceptar e modificar o tempo de execução do cliente, bem como as classes em que você pode inserir suas extensões personalizadas em aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="56c64-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="56c64-108">Por exemplo, executar o log de mensagens de cliente personalizadas, executar a serialização da mensagem personalizada e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="56c64-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="56c64-109">Estendendo distribuidores</span><span class="sxs-lookup"><span data-stu-id="56c64-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="56c64-110">Descreve as interfaces que podem interceptar e modificar o tempo de execução do serviço, bem como as classes em que você pode inserir suas extensões personalizadas em aplicativos de serviço.</span><span class="sxs-lookup"><span data-stu-id="56c64-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="56c64-111">Por exemplo, você pode executar o log de serviço personalizado, a validação do lado do serviço de mensagem, expedição personalizados e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="56c64-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="56c64-112">Objetos extensíveis</span><span class="sxs-lookup"><span data-stu-id="56c64-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="56c64-113">Descreve os cinco objetos extensíveis e o <xref:System.ServiceModel.IExtensibleObject%601> padrão.</span><span class="sxs-lookup"><span data-stu-id="56c64-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="56c64-114">O padrão de objeto extensível é usado para estender as classes de tempo de execução existentes com a nova funcionalidade ou para adicionar o novo estado para um objeto.</span><span class="sxs-lookup"><span data-stu-id="56c64-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="56c64-115">Extensões, anexadas a um dos objetos extensíveis, habilitar comportamentos em diferentes estágios de processamento para acessar o estado compartilhado e anexado a um objeto extensível comum que eles possam acessar a funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="56c64-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="56c64-116">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="56c64-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="56c64-117">Para alterar as configurações em ou inserir extensões no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tempo de execução, você usa comportamentos.</span><span class="sxs-lookup"><span data-stu-id="56c64-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="56c64-118">O WCF inclui comportamentos implementados pelo sistema para controlar a limitação de instanciação e muitos outros aspectos de serviços e operações.</span><span class="sxs-lookup"><span data-stu-id="56c64-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="56c64-119">Esta seção descreve como criar seus próprios comportamentos personalizados e como torná-los disponíveis tanto por meio de programação e usando arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="56c64-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="56c64-120">Estendendo a hospedagem com ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="56c64-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="56c64-121">Descreve como estender <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>e usar o <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes para personalizar o ambiente de host.</span><span class="sxs-lookup"><span data-stu-id="56c64-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="56c64-122">Referência</span><span class="sxs-lookup"><span data-stu-id="56c64-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="56c64-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="56c64-123">Related Sections</span></span>
