---
title: Federação
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e7aef1f53675089ee311aa79a54abf60441b728
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="federation"></a><span data-ttu-id="5c8d7-102">Federação</span><span class="sxs-lookup"><span data-stu-id="5c8d7-102">Federation</span></span>
<span data-ttu-id="5c8d7-103">Este tópico fornece uma visão geral sobre o conceito de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="5c8d7-104">Ele também descreve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suporte para implantação de arquiteturas de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-104">It also describes [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for deploying federated security architectures.</span></span> <span data-ttu-id="5c8d7-105">Para um aplicativo de exemplo que demonstra a federação, consulte [federação exemplo](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5c8d7-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="5c8d7-106">Definição da segurança federada</span><span class="sxs-lookup"><span data-stu-id="5c8d7-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="5c8d7-107">Segurança federada permite uma separação clara entre o serviço de que acesso a um cliente e os procedimentos de autenticação e autorização associados.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="5c8d7-108">Segurança federada também permite a colaboração entre vários sistemas, redes e organizações em diferentes realms de confiança.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="5c8d7-109"> fornece suporte para criação e implantação de sistemas distribuídos que utilizam segurança federada.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-109"> provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="5c8d7-110">Elementos de uma arquitetura de segurança federada</span><span class="sxs-lookup"><span data-stu-id="5c8d7-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="5c8d7-111">A arquitetura de segurança federada tem três elementos principais, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="5c8d7-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c8d7-112">Element</span></span>|<span data-ttu-id="5c8d7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c8d7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c8d7-114">Domínio/realm</span><span class="sxs-lookup"><span data-stu-id="5c8d7-114">Domain/realm</span></span>|<span data-ttu-id="5c8d7-115">Uma única unidade de administração de segurança ou confiança.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="5c8d7-116">Um domínio típico pode incluir uma única organização.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="5c8d7-117">Federação</span><span class="sxs-lookup"><span data-stu-id="5c8d7-117">Federation</span></span>|<span data-ttu-id="5c8d7-118">Uma coleção de domínios que tenham estabelecido confiança.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="5c8d7-119">O nível de confiança pode variar, mas normalmente inclui a autenticação e quase sempre inclui autorização.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="5c8d7-120">Uma federação típica pode incluir várias organizações que tenham estabelecido confiança de acesso compartilhado a um conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="5c8d7-121">STS (Serviço de Token de Segurança)</span><span class="sxs-lookup"><span data-stu-id="5c8d7-121">Security Token Service (STS)</span></span>|<span data-ttu-id="5c8d7-122">Um serviço Web que emite tokens de segurança; ou seja, ele faz declarações com base na evidência de que ele confia, para qualquer pessoa que confia nele.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="5c8d7-123">Isso constitui a base de intermediar a confiança entre domínios.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="5c8d7-124">Cenário de exemplo</span><span class="sxs-lookup"><span data-stu-id="5c8d7-124">Example Scenario</span></span>  
 <span data-ttu-id="5c8d7-125">A ilustração a seguir mostra um exemplo de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-125">The following illustration shows an example of federated security.</span></span>  
  
 <span data-ttu-id="5c8d7-126">![Federação](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span><span class="sxs-lookup"><span data-stu-id="5c8d7-126">![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span></span>  
  
 <span data-ttu-id="5c8d7-127">Este cenário inclui duas organizações: A e B. esta organização tem um recurso da Web (um serviço da Web) que alguns usuários na organização A ser valiosos.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c8d7-128">Esta seção usa os termos *recurso*, *service*, e *serviço Web* alternadamente.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="5c8d7-129">Normalmente, a organização B requer que um usuário da organização A fornecer alguma forma válida de autenticação antes de acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="5c8d7-130">Além disso, a organização também pode exigir que o usuário seja autorizado a acessar o recurso específico em questão.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="5c8d7-131">Uma maneira de resolver esse problema e permitir que os usuários na organização A acessar o recurso na organização B é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5c8d7-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
-   <span data-ttu-id="5c8d7-132">Os usuários da organização A registrar suas credenciais (um nome de usuário e senha) com a empresa B.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
-   <span data-ttu-id="5c8d7-133">Durante o acesso ao recurso, os usuários da organização A apresentam suas credenciais para a empresa B e são autenticados antes de acessar o recurso.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="5c8d7-134">Essa abordagem tem três desvantagens significativas:</span><span class="sxs-lookup"><span data-stu-id="5c8d7-134">This approach has three significant drawbacks:</span></span>  
  
-   <span data-ttu-id="5c8d7-135">Organização B precisa gerenciar as credenciais para que os usuários da organização A além de gerenciar as credenciais de seus usuários locais.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
-   <span data-ttu-id="5c8d7-136">Os usuários da organização A precisam manter um conjunto adicional de credenciais (ou seja, lembre-se de um nome de usuário e senha) além as credenciais que normalmente usam para acessar recursos na organização A. Isso geralmente incentiva a prática de usar o mesmo nome de usuário e senha em vários sites de serviço, que é uma medida de segurança fraca.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
-   <span data-ttu-id="5c8d7-137">A arquitetura não se expandir conforme mais organizações entendem o recurso na organização B como sendo de algum valor.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="5c8d7-138">Uma abordagem alternativa, que trata das desvantagens mencionadas anteriormente, é empregar segurança federada.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="5c8d7-139">Nessa abordagem, as organizações A e B estabelecer uma relação de confiança e empregam o serviço de Token de segurança (STS) para habilitar intermediar da relação de confiança estabelecida.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="5c8d7-140">Em uma arquitetura de segurança federada, a usuários da organização A saber que se deseja acessar o serviço Web na organização B que eles devem apresentar um token de segurança válido do STS na organização B, que autentica e autoriza o acesso para o serviço específico.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="5c8d7-141">Sobre como contatar o STS B, os usuários recebem outro nível de indireção a política associada com o STS.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="5c8d7-142">Ele devem apresentar uma segurança válido token da STS A (ou seja, o realm da relação de confiança do cliente) antes da STS B pode emitir a eles um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="5c8d7-143">Isso é resultado da relação de confiança estabelecida entre as duas organizações e implica que organização B não precisa gerenciar as identidades dos usuários da organização A. Na prática, o STS B geralmente tem um valor nulo `issuerAddress` e `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="5c8d7-144">Para obter mais informações, consulte [como: configurar um emissor Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="5c8d7-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="5c8d7-145">Nesse caso, o cliente consulta uma diretiva local para localizar STS A. Essa configuração é chamada *inicial da federação de território* e dimensiona melhor porque STS B não precisa manter informações sobre STS A.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="5c8d7-146">Os usuários, em seguida, entre em contato com o STS da organização A e obter um token de segurança apresentando credenciais de autenticação que normalmente usam para acessar qualquer outro recurso dentro da organização A. Isso também elimina o problema de usuários precisar manter vários conjuntos de credenciais ou usando o mesmo conjunto de credenciais em vários sites de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="5c8d7-147">Depois que os usuários obter um token de segurança da STS A, eles apresentam o token para o STS B. esta organização prossegue para executar a autorização de solicitações dos usuários e emite um token de segurança para os usuários do seu próprio conjunto de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="5c8d7-148">Os usuários, em seguida, podem apresentar seu token para o recurso na organização B e acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="5c8d7-149">Suporte para segurança federada no WCF</span><span class="sxs-lookup"><span data-stu-id="5c8d7-149">Support for Federated Security in WCF</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="5c8d7-150"> fornece suporte pronto para uso para implantação de arquiteturas de segurança federada por meio de [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5c8d7-150"> provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="5c8d7-151">O [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento fornece para uma associação segura, confiável e interoperável que envolve o uso de HTTP como o mecanismo de transporte subjacente para o estilo de comunicação de solicitação-resposta, empregando texto e XML como formato de conexão para a codificação.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="5c8d7-152">O uso de [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) em uma segurança federada cenário pode ser separado em duas fases logicamente independentes, conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="5c8d7-153">Fase 1: Fase de Design</span><span class="sxs-lookup"><span data-stu-id="5c8d7-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="5c8d7-154">Durante a fase de design, o cliente usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para ler a política que expõe o ponto de extremidade de serviço e para coletar os requisitos de autenticação e autorização do serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="5c8d7-155">Os proxies apropriados são construídos para criar o seguinte padrão de comunicação de segurança federada no cliente:</span><span class="sxs-lookup"><span data-stu-id="5c8d7-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
-   <span data-ttu-id="5c8d7-156">Obter um token de segurança do STS no território de confiança do cliente.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
-   <span data-ttu-id="5c8d7-157">Apresente o token para o STS no território de confiança do serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-157">Present the token to the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="5c8d7-158">Obter um token de segurança do STS no território de confiança do serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="5c8d7-159">Apresente o token para o serviço para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="5c8d7-160">Etapa 2: Fase de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5c8d7-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="5c8d7-161">Durante a fase de tempo de execução, o cliente cria um objeto de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe cliente e faz uma chamada usando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-161">During the run-time phase, the client instantiates an object of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class and makes a call using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="5c8d7-162">A estrutura subjacente do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lida com as etapas mencionadas anteriormente no padrão de comunicação de segurança federada e permite que o cliente perfeitamente consumir o serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-162">The underlying framework of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="5c8d7-163">Implementação de exemplo usando o WCF</span><span class="sxs-lookup"><span data-stu-id="5c8d7-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="5c8d7-164">A ilustração a seguir mostra uma implementação de exemplo para uma arquitetura de segurança federada usando o suporte nativo do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c8d7-164">The following illustration shows a sample implementation for a federated security architecture using native support from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="5c8d7-165">![Segurança de federação no WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span><span class="sxs-lookup"><span data-stu-id="5c8d7-165">![Federation security in WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span></span>  
  
### <a name="example-myservice"></a><span data-ttu-id="5c8d7-166">Exemplo MyService</span><span class="sxs-lookup"><span data-stu-id="5c8d7-166">Example MyService</span></span>  
 <span data-ttu-id="5c8d7-167">O serviço `MyService` expõe um ponto de extremidade por meio de `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="5c8d7-168">A ilustração a seguir mostra o endereço, associação e contrato associado com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 <span data-ttu-id="5c8d7-169">![Federação](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span><span class="sxs-lookup"><span data-stu-id="5c8d7-169">![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span></span>  
  
 <span data-ttu-id="5c8d7-170">O ponto de extremidade de serviço `MyServiceEndpoint` usa o [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e requer um token válido do Security asserções Markup Language (SAML) com um `accessAuthorized` declaração emitida pelo STS B. Isso é especificado de forma declarativa na configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"      
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata   
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization   
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="5c8d7-171">Um ponto sutil deve ser observado sobre as declarações necessárias por `MyService`.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="5c8d7-172">O segundo número indica que `MyService` requer um token SAML com o `accessAuthorized` de declaração.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="5c8d7-173">Para ser mais preciso, isso Especifica a declaração de tipo `MyService` requer.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="5c8d7-174">O nome totalmente qualificado desse tipo de declaração é http://tempuri.org:accessAuthorized (junto com o namespace associado), que é usado no arquivo de configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-174">The fully-qualified name of this claim type is http://tempuri.org:accessAuthorized (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="5c8d7-175">O valor da declaração indica a presença da declaração e deve ser definido como `true` pelo STS B.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="5c8d7-176">Em tempo de execução, essa política é imposta pelo `MyServiceOperationRequirement` que é implementado como parte da classe de `MyService`.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="5c8d7-177">STS B</span><span class="sxs-lookup"><span data-stu-id="5c8d7-177">STS B</span></span>  
 <span data-ttu-id="5c8d7-178">A ilustração a seguir mostra o STS B. Conforme mencionado anteriormente, um serviço de token de segurança (STS) também é um serviço Web e pode ter seus pontos de extremidade associados, política e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 <span data-ttu-id="5c8d7-179">![Federação](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span><span class="sxs-lookup"><span data-stu-id="5c8d7-179">![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span></span>  
  
 <span data-ttu-id="5c8d7-180">STS B expõe um ponto de extremidade, chamado `STSEndpoint` que podem ser usadas para solicitar tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="5c8d7-181">Especificamente, STS B emite tokens SAML com o `accessAuthorized` de declaração, que pode ser apresentado no `MyService` site de serviço para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="5c8d7-182">No entanto, STS B exige que os usuários a apresentar um token SAML válido emitido pelo STS A que contém o `userAuthenticated` de declaração.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="5c8d7-183">Isso é especificado de forma declarativa na configuração do STS.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="5c8d7-184">Novamente, o `userAuthenticated` declaração é o tipo de declaração que é exigido pelo STS B. O nome totalmente qualificado desse tipo de declaração é http://tempuri.org:userAuthenticated (junto com o namespace associado), que é usado no arquivo de configuração STS.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is http://tempuri.org:userAuthenticated (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="5c8d7-185">O valor da declaração indica a presença da declaração e deve ser definido como `true` pelo STS A.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="5c8d7-186">Em tempo de execução, o `STS_B_OperationRequirement` classe aplica essa política, que é implementada como parte do STS B.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="5c8d7-187">Se a verificação de acesso estiver desmarcada, STS B emite um token SAML com o `accessAuthorized` de declaração.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="5c8d7-188">STS UM</span><span class="sxs-lookup"><span data-stu-id="5c8d7-188">STS A</span></span>  
 <span data-ttu-id="5c8d7-189">A ilustração a seguir mostra o STS A.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="5c8d7-190">![Federação](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="5c8d7-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="5c8d7-191">Semelhante do STS B, o STS A também é um serviço Web que emite tokens de segurança e expõe um ponto de extremidade para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="5c8d7-192">No entanto, ele usa uma associação diferente (`wsHttpBinding`) e requer que os usuários apresentem válido [!INCLUDE[infocard](../../../../includes/infocard-md.md)] com um `emailAddress` de declaração.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="5c8d7-193">Em resposta, ele emite tokens SAML com o `userAuthenticated` de declaração.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="5c8d7-194">Isso é especificado de forma declarativa na configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"    
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"   
                       storeName="My" />  
       </identity>  
    <endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5c8d7-195">Em tempo de execução, o `STS_A_OperationRequirement` classe aplica essa política, que é implementada como parte do STS A.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="5c8d7-196">Se o acesso é `true`, STS A emite um token SAML com `userAuthenticated` de declaração.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="5c8d7-197">Cliente da organização A</span><span class="sxs-lookup"><span data-stu-id="5c8d7-197">Client at Organization A</span></span>  
 <span data-ttu-id="5c8d7-198">A ilustração a seguir mostra o cliente na organização A, junto com as etapas envolvidas na criação um `MyService` chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="5c8d7-199">Os outros componentes funcionais também estão incluídos para fins de integridade.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-199">The other functional components are also included for completeness.</span></span>  
  
 <span data-ttu-id="5c8d7-200">![Federação](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span><span class="sxs-lookup"><span data-stu-id="5c8d7-200">![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="5c8d7-201">Resumo</span><span class="sxs-lookup"><span data-stu-id="5c8d7-201">Summary</span></span>  
 <span data-ttu-id="5c8d7-202">Segurança federada fornece uma divisão limpa de responsabilidade e ajuda a criar arquiteturas de serviço segura e escalonável.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="5c8d7-203">Como uma plataforma para criar e implantar aplicativos distribuídos, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece suporte nativo para implementar segurança federada.</span><span class="sxs-lookup"><span data-stu-id="5c8d7-203">As a platform for building and deploying distributed applications, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8d7-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c8d7-204">See Also</span></span>  
 [<span data-ttu-id="5c8d7-205">Segurança</span><span class="sxs-lookup"><span data-stu-id="5c8d7-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
