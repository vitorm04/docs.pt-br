---
title: Federação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: 2331e484f22be7e3154a4cff981ee320a9b143a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948152"
---
# <a name="federation"></a><span data-ttu-id="0c1eb-102">Federação</span><span class="sxs-lookup"><span data-stu-id="0c1eb-102">Federation</span></span>
<span data-ttu-id="0c1eb-103">Este tópico fornece uma breve visão geral do conceito de segurança federada.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="0c1eb-104">Ele também descreve o suporte a Windows Communication Foundation (WCF) para implantar arquiteturas de segurança federadas.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="0c1eb-105">Para obter um aplicativo de exemplo que demonstre a Federação, consulte [exemplo de Federação](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0c1eb-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="0c1eb-106">Definição de segurança federada</span><span class="sxs-lookup"><span data-stu-id="0c1eb-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="0c1eb-107">A segurança federada permite uma separação clara entre o serviço que um cliente está acessando e os procedimentos de autenticação e autorização associados.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="0c1eb-108">A segurança federada também permite a colaboração entre vários sistemas, redes e organizações em territórios de confiança diferentes.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="0c1eb-109">O WCF oferece suporte para a criação e implantação de sistemas distribuídos que empregam a segurança federada.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="0c1eb-110">Elementos de uma arquitetura de segurança federada</span><span class="sxs-lookup"><span data-stu-id="0c1eb-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="0c1eb-111">A arquitetura de segurança federada tem três elementos principais, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="0c1eb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c1eb-112">Element</span></span>|<span data-ttu-id="0c1eb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c1eb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c1eb-114">Domínio/realm</span><span class="sxs-lookup"><span data-stu-id="0c1eb-114">Domain/realm</span></span>|<span data-ttu-id="0c1eb-115">Uma única unidade de administração ou confiança de segurança.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="0c1eb-116">Um domínio típico pode incluir uma única organização.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="0c1eb-117">Federação</span><span class="sxs-lookup"><span data-stu-id="0c1eb-117">Federation</span></span>|<span data-ttu-id="0c1eb-118">Uma coleção de domínios que estabeleceram confiança.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="0c1eb-119">O nível de confiança pode variar, mas normalmente inclui autenticação e quase sempre inclui autorização.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="0c1eb-120">Uma federação típica pode incluir várias organizações que estabeleceram confiança para acesso compartilhado a um conjunto de recursos.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="0c1eb-121">STS (Serviço de Token de Segurança)</span><span class="sxs-lookup"><span data-stu-id="0c1eb-121">Security Token Service (STS)</span></span>|<span data-ttu-id="0c1eb-122">Um serviço Web que emite tokens de segurança; ou seja, ele faz asserções com base nas evidências que confiam, para quemá-la a confiar.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="0c1eb-123">Isso constitui a base do agente de confiança entre domínios.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="0c1eb-124">Cenário de exemplo</span><span class="sxs-lookup"><span data-stu-id="0c1eb-124">Example Scenario</span></span>  
 <span data-ttu-id="0c1eb-125">A ilustração a seguir mostra um exemplo de segurança federada:</span><span class="sxs-lookup"><span data-stu-id="0c1eb-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Diagrama mostrando um cenário típico de segurança federada.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="0c1eb-127">Esse cenário inclui duas organizações: A e B. a organização B tem um recurso da Web (um serviço Web) que alguns usuários da organização A encontrem valiosos.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c1eb-128">Esta seção usa o *recurso*de termos, o *serviço*e o *serviço Web* de maneira intercambiável.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="0c1eb-129">Normalmente, a organização B requer que um usuário da organização A forneça alguma forma válida de autenticação antes de acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="0c1eb-130">Além disso, a organização também pode exigir que o usuário esteja autorizado a acessar o recurso específico em questão.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="0c1eb-131">Uma maneira de resolver esse problema e permitir que os usuários na organização a acessem o recurso na organização B é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0c1eb-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="0c1eb-132">Os usuários da organização A registram suas credenciais (um nome de usuário e senha) com a organização B.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="0c1eb-133">Durante o acesso aos recursos, os usuários da organização A apresentam suas credenciais para a organização B e são autenticados antes de acessar o recurso.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="0c1eb-134">Essa abordagem tem três desvantagens significativas:</span><span class="sxs-lookup"><span data-stu-id="0c1eb-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="0c1eb-135">A organização B precisa gerenciar as credenciais de usuários da organização A, além de gerenciar as credenciais de seus usuários locais.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="0c1eb-136">Os usuários da organização precisam manter um conjunto adicional de credenciais (ou seja, lembrar-se de um nome de usuário e senha adicionais) Além das credenciais que normalmente usam para obter acesso aos recursos da organização A. Isso geralmente incentiva a prática de usar o mesmo nome de usuário e senha em vários sites de serviço, o que é uma medida de segurança fraca.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="0c1eb-137">A arquitetura não é dimensionada conforme mais organizações percebem o recurso na organização B como sendo de algum valor.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="0c1eb-138">Uma abordagem alternativa, que aborda as desvantagens mencionadas anteriormente, é empregar a segurança federada.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="0c1eb-139">Nessa abordagem, as organizações A e B estabelecem uma relação de confiança e empregam o serviço de token de segurança (STS) para habilitar o agente da confiança estabelecida.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="0c1eb-140">Em uma arquitetura de segurança federada, os usuários da organização sabem que se desejarem acessar o serviço Web na organização B que eles devem apresentar um token de segurança válido do STS na organização B, que autentica e autoriza seu acesso ao serviço específico.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="0c1eb-141">Ao entrar em contato com o STS B, os usuários recebem outro nível de indireção da política associada ao STS.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="0c1eb-142">Eles devem apresentar um token de segurança válido do STS A (ou seja, o realm de confiança do cliente) antes que o STS B possa emitir um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="0c1eb-143">Trata-se de um registro da relação de confiança estabelecida entre as duas organizações e implica que a organização B não precisa gerenciar identidades para usuários da organização A. Na prática, o STS B geralmente tem um `issuerAddress` valor `issuerMetadataAddress`nulo e.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="0c1eb-144">Para obter mais informações, confira [Como: Configure um emissor](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)local.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="0c1eb-145">Nesse caso, o cliente consulta uma política local para localizar o STS A. Essa configuração é chamada de *Federação de realm inicial* e dimensiona melhor porque o STS B não precisa manter informações sobre o STS a.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="0c1eb-146">Em seguida, os usuários entram em contato com o STS na organização A e obtêm um token de segurança apresentando as credenciais de autenticação que eles normalmente usam para obter acesso a qualquer outro recurso na organização A. Isso também alivia o problema de usuários que têm de manter vários conjuntos de credenciais ou usando o mesmo conjunto de credenciais em vários sites de serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="0c1eb-147">Depois que os usuários obtêm um token de segurança do STS A, eles apresentam o token para o STS B. a organização B continua a executar a autorização das solicitações dos usuários e emite um token de segurança para os usuários de seu próprio conjunto de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="0c1eb-148">Os usuários podem então apresentar seu token para o recurso na organização B e acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="0c1eb-149">Suporte para segurança federada no WCF</span><span class="sxs-lookup"><span data-stu-id="0c1eb-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="0c1eb-150">O WCF fornece suporte completo para implantar arquiteturas de segurança federada por meio do [ \<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0c1eb-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="0c1eb-151">O elemento WSFederationHttpBinding > fornece uma associação segura, confiável e interoperável que envolve o uso de http como o mecanismo de transporte subjacente para o estilo de comunicação de solicitação-resposta, o emprego de texto e XML como o [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) formato de conexão para codificação.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="0c1eb-152">O uso de [ \<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) em um cenário de segurança federada pode ser dissociado em duas fases logicamente independentes, conforme descrito nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="0c1eb-153">Fase 1: Fase de design</span><span class="sxs-lookup"><span data-stu-id="0c1eb-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="0c1eb-154">Durante a fase de design, o cliente usa a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para ler a política que o ponto de extremidade de serviço expõe e para coletar os requisitos de autenticação e autorização do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="0c1eb-155">Os proxies apropriados são construídos para criar o seguinte padrão de comunicação de segurança federada no cliente:</span><span class="sxs-lookup"><span data-stu-id="0c1eb-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="0c1eb-156">Obtenha um token de segurança do STS no realm de confiança do cliente.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="0c1eb-157">Apresente o token para o STS no realm de confiança do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="0c1eb-158">Obtenha um token de segurança do STS no realm de confiança do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="0c1eb-159">Apresente o token ao serviço para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="0c1eb-160">Fase 2: Fase de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0c1eb-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="0c1eb-161">Durante a fase de tempo de execução, o cliente cria uma instância de um objeto da classe WCF Client e faz uma chamada usando o cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="0c1eb-162">A estrutura subjacente do WCF manipula as etapas mencionadas anteriormente no padrão de comunicação de segurança federada e permite que o cliente consuma o serviço diretamente.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="0c1eb-163">Exemplo de implementação usando o WCF</span><span class="sxs-lookup"><span data-stu-id="0c1eb-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="0c1eb-164">A ilustração a seguir mostra uma implementação de exemplo para uma arquitetura de segurança federada usando o suporte nativo do WCF.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Diagrama mostrando uma implementação de segurança de Federação de exemplo.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="0c1eb-166">Exemplo de MyService</span><span class="sxs-lookup"><span data-stu-id="0c1eb-166">Example MyService</span></span>  
 <span data-ttu-id="0c1eb-167">O serviço `MyService` expõe um único ponto de `MyServiceEndpoint`extremidade por meio do.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="0c1eb-168">A ilustração a seguir mostra o endereço, a associação e o contrato associados ao ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![Diagrama mostrando os detalhes de myserviceendpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="0c1eb-170">O ponto de `MyServiceEndpoint` extremidade de serviço usa o [ \<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e requer um token SAML (Security asserties Markup Language) `accessAuthorized` válido com uma declaração emitida pelo STS B. Isso é declarativamente especificado na configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
> <span data-ttu-id="0c1eb-171">Um ponto sutil deve ser observado sobre as declarações exigidas `MyService`pelo.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="0c1eb-172">A segunda figura indica que `MyService` o requer um token SAML com `accessAuthorized` a declaração.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="0c1eb-173">Para ser mais preciso, isso especifica o tipo de Declaração `MyService` que o requer.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="0c1eb-174">O nome totalmente qualificado desse tipo de declaração é `http://tempuri.org:accessAuthorized` (junto com o namespace associado), que é usado no arquivo de configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="0c1eb-175">O valor dessa declaração indica a presença dessa declaração e é considerado como definido `true` pelo STS B.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="0c1eb-176">Em tempo de execução, essa política é imposta pela `MyServiceOperationRequirement` classe que é implementada como parte `MyService`do.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="0c1eb-177">STS B</span><span class="sxs-lookup"><span data-stu-id="0c1eb-177">STS B</span></span>  
 <span data-ttu-id="0c1eb-178">A ilustração a seguir mostra o STS B. Como mencionado anteriormente, um STS (serviço de token de segurança) também é um serviço Web e pode ter seus pontos de extremidade associados, política e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Diagrama mostrando o serviço de token de segurança B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="0c1eb-180">O STS B expõe um único ponto de `STSEndpoint` extremidade, chamado que pode ser usado para solicitar tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="0c1eb-181">Especificamente, o STS B emite tokens SAML `accessAuthorized` com a declaração, que pode ser apresentada `MyService` no site do serviço para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="0c1eb-182">No entanto, o STS B exige que os usuários apresentem um token SAML válido emitido pelo `userAuthenticated` STS a que contém a declaração.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="0c1eb-183">Isso é declarativamente especificado na configuração do STS.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
> <span data-ttu-id="0c1eb-184">Novamente, a `userAuthenticated` declaração é o tipo de declaração exigido pelo STS B. O nome totalmente qualificado desse tipo de declaração é `http://tempuri.org:userAuthenticated` (junto com o namespace associado), que é usado no arquivo de configuração do STS.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="0c1eb-185">O valor dessa declaração indica a presença dessa declaração e é considerado como definido `true` pelo STS a.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="0c1eb-186">Em tempo de execução `STS_B_OperationRequirement` , a classe impõe essa política, que é implementada como parte do STS B.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="0c1eb-187">Se a verificação de acesso estiver clara, o STS B emitirá um token `accessAuthorized` SAML com a declaração.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="0c1eb-188">STS A</span><span class="sxs-lookup"><span data-stu-id="0c1eb-188">STS A</span></span>  
 <span data-ttu-id="0c1eb-189">A ilustração a seguir mostra o STS A.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="0c1eb-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="0c1eb-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="0c1eb-191">Semelhante ao STS B, o STS a também é um serviço Web que emite tokens de segurança e expõe um único ponto de extremidade para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="0c1eb-192">No entanto, ele usa uma associação`wsHttpBinding`diferente () e exige que os usuários apresentem um `emailAddress` CardSpace válido com uma declaração.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="0c1eb-193">Em resposta, ele emite tokens SAML com `userAuthenticated` a declaração.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="0c1eb-194">Isso é declarativamente especificado na configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="0c1eb-195">Em tempo de execução `STS_A_OperationRequirement` , a classe impõe essa política, que é implementada como parte do STS A.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="0c1eb-196">Se o acesso for `true`, o STS A emite um token SAML `userAuthenticated` com Claim.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="0c1eb-197">Cliente na organização A</span><span class="sxs-lookup"><span data-stu-id="0c1eb-197">Client at Organization A</span></span>  
 <span data-ttu-id="0c1eb-198">A ilustração a seguir mostra o cliente na organização a, juntamente com as etapas envolvidas em fazer `MyService` uma chamada de serviço.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="0c1eb-199">Os outros componentes funcionais também estão incluídos para fins de integridade.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-199">The other functional components are also included for completeness.</span></span>  
  
 ![Diagrama mostrando as etapas em uma chamada de serviço de MyService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="0c1eb-201">Resumo</span><span class="sxs-lookup"><span data-stu-id="0c1eb-201">Summary</span></span>  
 <span data-ttu-id="0c1eb-202">A segurança federada fornece uma divisão de responsabilidade limpa e ajuda a criar arquiteturas de serviço seguras e escalonáveis.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="0c1eb-203">Como uma plataforma para a criação e implantação de aplicativos distribuídos, o WCF fornece suporte nativo para implementar a segurança federada.</span><span class="sxs-lookup"><span data-stu-id="0c1eb-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c1eb-204">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c1eb-204">See also</span></span>

- [<span data-ttu-id="0c1eb-205">Segurança</span><span class="sxs-lookup"><span data-stu-id="0c1eb-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
