---
title: Estendendo o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 24ad74f04a3ac31d0b0d0d87f0d74f88c0521f50
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="extending-wcf"></a><span data-ttu-id="ba9ab-102">Estendendo o WCF</span><span class="sxs-lookup"><span data-stu-id="ba9ab-102">Extending WCF</span></span>
<span data-ttu-id="ba9ab-103">Windows Communication Foundation (WCF) permite que você modifique e estender os componentes de tempo de execução para controlar com precisão e estender aplicativos baseados em serviço.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="ba9ab-104">Os tópicos nesta seção vá em detalhes sobre a arquitetura de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="ba9ab-105">Para obter mais informações sobre programação básica, consulte [básicas de programação WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="ba9ab-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba9ab-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ba9ab-106">In This Section</span></span>  
 [<span data-ttu-id="ba9ab-107">Estendendo ServiceHost e a camada de modelo de serviço</span><span class="sxs-lookup"><span data-stu-id="ba9ab-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="ba9ab-108">A camada de modelo de serviço é responsável por recebendo mensagens de entrada fora dos canais subjacentes, convertendo-os em invocações do método no código do aplicativo e enviar os resultados de volta para o chamador.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="ba9ab-109">Extensões do modelo de serviço modificam ou implementam a execução ou o comportamento de comunicação e recursos que envolvem a funcionalidade de dispatcher, comportamentos personalizados, mensagem e interceptação de parâmetro e outras funcionalidades de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="ba9ab-110">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="ba9ab-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="ba9ab-111">Associações são objetos que descrevem os detalhes de comunicação necessários para conectar a um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="ba9ab-112">Extensões de associação ou associações personalizadas implementam a funcionalidade de comunicação personalizados necessária para dar suporte a recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="ba9ab-113">Estendendo a camada do canal</span><span class="sxs-lookup"><span data-stu-id="ba9ab-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="ba9ab-114">A camada do canal fica abaixo da camada de modelo de serviço e é responsável pela troca de mensagens entre clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="ba9ab-115">Extensões de canal podem implementar a nova funcionalidade de protocolo, como a segurança.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="ba9ab-116">Extensões de canal de transporte também funcionalidades, como implementar um novo transporte de rede para transportar mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="ba9ab-117">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="ba9ab-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="ba9ab-118">Segurança no WCF consiste de transferência de segurança (integridade, confidencialidade e autenticação), controle de acesso (autorização) e auditoria.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="ba9ab-119">As classes encontradas no `IdentityModel` namespace são usados pelo WCF para controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="ba9ab-120">Noções básicas sobre a arquitetura de segurança permite que você crie tipos de declaração personalizada para acomodar sistemas de controle de acesso personalizados.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="ba9ab-121">Estendendo o sistema de metadados</span><span class="sxs-lookup"><span data-stu-id="ba9ab-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="ba9ab-122">O sistema de metadados do WCF é um grupo de interfaces e classes que representam os metadados necessários para implementar aplicativos baseados em serviço.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="ba9ab-123">Modificar ou estender as classes de ou implementar e configurar as interfaces para exportar e importar metadados personalizados, como extensões WSDL Web Services Description Language () ou asserções de WS-PolicyAttachments personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="ba9ab-124">Estendendo codificadores e serializadores</span><span class="sxs-lookup"><span data-stu-id="ba9ab-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="ba9ab-125">Serializadores e codificadores convertem dados de um formulário para outro.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="ba9ab-126">Os tópicos nesta seção abordam como estender as classes fornecidas para atender aos requisitos especiais.</span><span class="sxs-lookup"><span data-stu-id="ba9ab-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ba9ab-127">Referência</span><span class="sxs-lookup"><span data-stu-id="ba9ab-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="ba9ab-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ba9ab-128">Related Sections</span></span>  
 [<span data-ttu-id="ba9ab-129">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="ba9ab-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="ba9ab-130">Detalhes de recursos do WCF</span><span class="sxs-lookup"><span data-stu-id="ba9ab-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="ba9ab-131">Diretrizes e práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="ba9ab-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
