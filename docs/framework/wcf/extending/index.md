---
title: Estendendo o WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 037182a3cb105f544e15a05f955c142ba57f62f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795544"
---
# <a name="extending-wcf"></a><span data-ttu-id="6c7cc-102">Estendendo o WCF</span><span class="sxs-lookup"><span data-stu-id="6c7cc-102">Extending WCF</span></span>
<span data-ttu-id="6c7cc-103">O Windows Communication Foundation (WCF) permite que você modifique e estenda os componentes de tempo de execução para controlar e estender precisamente os aplicativos baseados em serviço.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="6c7cc-104">Os tópicos nesta seção se aprofundam em detalhes sobre a arquitetura de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="6c7cc-105">Para obter mais informações sobre programação básica, consulte [programação básica do WCF](../basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="6c7cc-105">For more information about basic programming, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c7cc-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6c7cc-106">In This Section</span></span>  
 [<span data-ttu-id="6c7cc-107">Estendendo ServiceHost e a camada de modelo de serviço</span><span class="sxs-lookup"><span data-stu-id="6c7cc-107">Extending ServiceHost and the Service Model Layer</span></span>](extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="6c7cc-108">A camada do modelo de serviço é responsável por extrair mensagens de entrada dos canais subjacentes, traduzi-las em invocações de método no código do aplicativo e enviar os resultados de volta para o chamador.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="6c7cc-109">As extensões de modelo de serviço modificam ou implementam o comportamento de execução ou de comunicação e recursos que envolvem a funcionalidade do Dispatcher, comportamentos personalizados, interceptação de mensagem e de parâmetro e outras funcionalidades de extensibilidade.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="6c7cc-110">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="6c7cc-110">Extending Bindings</span></span>](extending-bindings.md)  
 <span data-ttu-id="6c7cc-111">Associações são objetos que descrevem os detalhes de comunicação necessários para se conectar a um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="6c7cc-112">Extensões de associação ou associações personalizadas implementam a funcionalidade de comunicação personalizada necessária para dar suporte aos recursos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="6c7cc-113">Estendendo a camada do canal</span><span class="sxs-lookup"><span data-stu-id="6c7cc-113">Extending the Channel Layer</span></span>](extending-the-channel-layer.md)  
 <span data-ttu-id="6c7cc-114">A camada de canal fica abaixo da camada de modelo de serviço e é responsável pela troca de mensagens entre clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="6c7cc-115">As extensões de canal podem implementar a nova funcionalidade de protocolo, como segurança.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="6c7cc-116">As extensões de canal também transportam a funcionalidade, como a implementação de um novo transporte de rede para transportar mensagens SOAP.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="6c7cc-117">Estendendo a segurança</span><span class="sxs-lookup"><span data-stu-id="6c7cc-117">Extending Security</span></span>](extending-security.md)  
 <span data-ttu-id="6c7cc-118">A segurança no WCF consiste em segurança de transferência (integridade, confidencialidade e autenticação), controle de acesso (autorização) e auditoria.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="6c7cc-119">As classes encontradas no `IdentityModel` namespace são usadas pelo WCF para controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="6c7cc-120">Entender a arquitetura de segurança permite que você crie tipos de declaração personalizados para acomodar sistemas de controle de acesso personalizados.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="6c7cc-121">Estendendo o sistema de metadados</span><span class="sxs-lookup"><span data-stu-id="6c7cc-121">Extending the Metadata System</span></span>](extending-the-metadata-system.md)  
 <span data-ttu-id="6c7cc-122">O sistema de metadados do WCF é um grupo de classes e interfaces que representam os metadados necessários para implementar aplicativos baseados em serviço.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="6c7cc-123">Modifique ou estenda as classes ou implemente e configure as interfaces para exportar e importar metadados personalizados, como as extensões WSDL (Web Services Description Language) ou as asserções WS-PolicyAttachments personalizadas.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="6c7cc-124">Estendendo codificadores e serializadores</span><span class="sxs-lookup"><span data-stu-id="6c7cc-124">Extending Encoders and Serializers</span></span>](extending-encoders-and-serializers.md)  
 <span data-ttu-id="6c7cc-125">Codificadores e serializadores convertem dados de um formulário para outro.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="6c7cc-126">Os tópicos nesta seção discutem como estender as classes fornecidas para atender aos requisitos especiais.</span><span class="sxs-lookup"><span data-stu-id="6c7cc-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6c7cc-127">Referência</span><span class="sxs-lookup"><span data-stu-id="6c7cc-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="6c7cc-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6c7cc-128">Related Sections</span></span>  
 [<span data-ttu-id="6c7cc-129">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="6c7cc-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="6c7cc-130">Detalhes de recursos do WCF</span><span class="sxs-lookup"><span data-stu-id="6c7cc-130">WCF Feature Details</span></span>](../feature-details/index.md)  
  
 [<span data-ttu-id="6c7cc-131">Diretrizes e práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="6c7cc-131">Guidelines and Best Practices</span></span>](../guidelines-and-best-practices.md)
