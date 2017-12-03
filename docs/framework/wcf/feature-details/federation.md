---
title: "Federação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9b707108d5849db57dcebfb4cb1f7b18378bff0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="federation"></a>Federação
Este tópico fornece uma visão geral sobre o conceito de segurança federada. Ele também descreve [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suporte para implantação de arquiteturas de segurança federada. Para um aplicativo de exemplo que demonstra a federação, consulte [federação exemplo](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definição da segurança federada  
 Segurança federada permite uma separação clara entre o serviço de que acesso a um cliente e os procedimentos de autenticação e autorização associados. Segurança federada também permite a colaboração entre vários sistemas, redes e organizações em diferentes realms de confiança.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece suporte para criação e implantação de sistemas distribuídos que utilizam segurança federada.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Elementos de uma arquitetura de segurança federada  
 A arquitetura de segurança federada tem três elementos principais, conforme descrito na tabela a seguir.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Domínio/realm|Uma única unidade de administração de segurança ou confiança. Um domínio típico pode incluir uma única organização.|  
|Federação|Uma coleção de domínios que tenham estabelecido confiança. O nível de confiança pode variar, mas normalmente inclui a autenticação e quase sempre inclui autorização. Uma federação típica pode incluir várias organizações que tenham estabelecido confiança de acesso compartilhado a um conjunto de recursos.|  
|STS (Serviço de Token de Segurança)|Um serviço Web que emite tokens de segurança; ou seja, ele faz declarações com base na evidência de que ele confia, para qualquer pessoa que confia nele. Isso constitui a base de intermediar a confiança entre domínios.|  
  
### <a name="example-scenario"></a>Cenário de exemplo  
 A ilustração a seguir mostra um exemplo de segurança federada.  
  
 ![Federação](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")  
  
 Este cenário inclui duas organizações: A e B. esta organização tem um recurso da Web (um serviço da Web) que alguns usuários na organização A ser valiosos.  
  
> [!NOTE]
>  Esta seção usa os termos *recurso*, *service*, e *serviço Web* alternadamente.  
  
 Normalmente, a organização B requer que um usuário da organização A fornecer alguma forma válida de autenticação antes de acessar o serviço. Além disso, a organização também pode exigir que o usuário seja autorizado a acessar o recurso específico em questão. Uma maneira de resolver esse problema e permitir que os usuários na organização A acessar o recurso na organização B é o seguinte:  
  
-   Os usuários da organização A registrar suas credenciais (um nome de usuário e senha) com a empresa B.  
  
-   Durante o acesso ao recurso, os usuários da organização A apresentam suas credenciais para a empresa B e são autenticados antes de acessar o recurso.  
  
 Essa abordagem tem três desvantagens significativas:  
  
-   Organização B precisa gerenciar as credenciais para que os usuários da organização A além de gerenciar as credenciais de seus usuários locais.  
  
-   Os usuários da organização A precisam manter um conjunto adicional de credenciais (ou seja, lembre-se de um nome de usuário e senha) além as credenciais que normalmente usam para acessar recursos na organização A. Isso geralmente incentiva a prática de usar o mesmo nome de usuário e senha em vários sites de serviço, que é uma medida de segurança fraca.  
  
-   A arquitetura não se expandir conforme mais organizações entendem o recurso na organização B como sendo de algum valor.  
  
 Uma abordagem alternativa, que trata das desvantagens mencionadas anteriormente, é empregar segurança federada. Nessa abordagem, as organizações A e B estabelecer uma relação de confiança e empregam o serviço de Token de segurança (STS) para habilitar intermediar da relação de confiança estabelecida.  
  
 Em uma arquitetura de segurança federada, a usuários da organização A saber que se deseja acessar o serviço Web na organização B que eles devem apresentar um token de segurança válido do STS na organização B, que autentica e autoriza o acesso para o serviço específico.  
  
 Sobre como contatar o STS B, os usuários recebem outro nível de indireção a política associada com o STS. Ele devem apresentar uma segurança válido token da STS A (ou seja, o realm da relação de confiança do cliente) antes da STS B pode emitir a eles um token de segurança. Isso é resultado da relação de confiança estabelecida entre as duas organizações e implica que organização B não precisa gerenciar as identidades dos usuários da organização A. Na prática, o STS B geralmente tem um valor nulo `issuerAddress` e `issuerMetadataAddress`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Como: configurar um emissor Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). Nesse caso, o cliente consulta uma diretiva local para localizar STS A. Essa configuração é chamada *inicial da federação de território* e dimensiona melhor porque STS B não precisa manter informações sobre STS A.  
  
 Os usuários, em seguida, entre em contato com o STS da organização A e obter um token de segurança apresentando credenciais de autenticação que normalmente usam para acessar qualquer outro recurso dentro da organização A. Isso também elimina o problema de usuários precisar manter vários conjuntos de credenciais ou usando o mesmo conjunto de credenciais em vários sites de serviço.  
  
 Depois que os usuários obter um token de segurança da STS A, eles apresentam o token para o STS B. esta organização prossegue para executar a autorização de solicitações dos usuários e emite um token de segurança para os usuários do seu próprio conjunto de tokens de segurança. Os usuários, em seguida, podem apresentar seu token para o recurso na organização B e acessar o serviço.  
  
## <a name="support-for-federated-security-in-wcf"></a>Suporte para segurança federada no WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece suporte pronto para uso para implantação de arquiteturas de segurança federada por meio de [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 O [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento fornece para uma associação segura, confiável e interoperável que envolve o uso de HTTP como o mecanismo de transporte subjacente para o estilo de comunicação de solicitação-resposta, empregando texto e XML como formato de conexão para a codificação.  
  
 O uso de [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) em uma segurança federada cenário pode ser separado em duas fases logicamente independentes, conforme descrito nas seções a seguir.  
  
### <a name="phase-1-design-phase"></a>Fase 1: Fase de Design  
 Durante a fase de design, o cliente usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para ler a política que expõe o ponto de extremidade de serviço e para coletar os requisitos de autenticação e autorização do serviço. Os proxies apropriados são construídos para criar o seguinte padrão de comunicação de segurança federada no cliente:  
  
-   Obter um token de segurança do STS no território de confiança do cliente.  
  
-   Apresente o token para o STS no território de confiança do serviço.  
  
-   Obter um token de segurança do STS no território de confiança do serviço.  
  
-   Apresente o token para o serviço para acessar o serviço.  
  
### <a name="phase-2-run-time-phase"></a>Etapa 2: Fase de tempo de execução  
 Durante a fase de tempo de execução, o cliente cria um objeto de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] classe cliente e faz uma chamada usando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente. A estrutura subjacente do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lida com as etapas mencionadas anteriormente no padrão de comunicação de segurança federada e permite que o cliente perfeitamente consumir o serviço.  
  
## <a name="sample-implementation-using-wcf"></a>Implementação de exemplo usando o WCF  
 A ilustração a seguir mostra uma implementação de exemplo para uma arquitetura de segurança federada usando o suporte nativo do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 ![Segurança de federação no WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")  
  
### <a name="example-myservice"></a>Exemplo MyService  
 O serviço `MyService` expõe um ponto de extremidade por meio de `MyServiceEndpoint`. A ilustração a seguir mostra o endereço, associação e contrato associado com o ponto de extremidade.  
  
 ![Federação](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")  
  
 O ponto de extremidade de serviço `MyServiceEndpoint` usa o [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e requer um token válido do Security asserções Markup Language (SAML) com um `accessAuthorized` declaração emitida pelo STS B. Isso é especificado de forma declarativa na configuração do serviço.  
  
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
>  Um ponto sutil deve ser observado sobre as declarações necessárias por `MyService`. O segundo número indica que `MyService` requer um token SAML com o `accessAuthorized` de declaração. Para ser mais preciso, isso Especifica a declaração de tipo `MyService` requer. O nome totalmente qualificado desse tipo de declaração é http://tempuri.org:accessAuthorized (junto com o namespace associado), que é usado no arquivo de configuração de serviço. O valor da declaração indica a presença da declaração e deve ser definido como `true` pelo STS B.  
  
 Em tempo de execução, essa política é imposta pelo `MyServiceOperationRequirement` que é implementado como parte da classe de `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 A ilustração a seguir mostra o STS B. Conforme mencionado anteriormente, um serviço de token de segurança (STS) também é um serviço Web e pode ter seus pontos de extremidade associados, política e assim por diante.  
  
 ![Federação](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")  
  
 STS B expõe um ponto de extremidade, chamado `STSEndpoint` que podem ser usadas para solicitar tokens de segurança. Especificamente, STS B emite tokens SAML com o `accessAuthorized` de declaração, que pode ser apresentado no `MyService` site de serviço para acessar o serviço. No entanto, STS B exige que os usuários a apresentar um token SAML válido emitido pelo STS A que contém o `userAuthenticated` de declaração. Isso é especificado de forma declarativa na configuração do STS.  
  
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
>  Novamente, o `userAuthenticated` declaração é o tipo de declaração que é exigido pelo STS B. O nome totalmente qualificado desse tipo de declaração é http://tempuri.org:userAuthenticated (junto com o namespace associado), que é usado no arquivo de configuração STS. O valor da declaração indica a presença da declaração e deve ser definido como `true` pelo STS A.  
  
 Em tempo de execução, o `STS_B_OperationRequirement` classe aplica essa política, que é implementada como parte do STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Se a verificação de acesso estiver desmarcada, STS B emite um token SAML com o `accessAuthorized` de declaração.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS UM  
 A ilustração a seguir mostra o STS A.  
  
 ![Federação](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Semelhante do STS B, o STS A também é um serviço Web que emite tokens de segurança e expõe um ponto de extremidade para essa finalidade. No entanto, ele usa uma associação diferente (`wsHttpBinding`) e requer que os usuários apresentem válido [!INCLUDE[infocard](../../../../includes/infocard-md.md)] com um `emailAddress` de declaração. Em resposta, ele emite tokens SAML com o `userAuthenticated` de declaração. Isso é especificado de forma declarativa na configuração do serviço.  
  
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
  
 Em tempo de execução, o `STS_A_OperationRequirement` classe aplica essa política, que é implementada como parte do STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Se o acesso é `true`, STS A emite um token SAML com `userAuthenticated` de declaração.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Cliente da organização A  
 A ilustração a seguir mostra o cliente na organização A, junto com as etapas envolvidas na criação um `MyService` chamada de serviço. Os outros componentes funcionais também estão incluídos para fins de integridade.  
  
 ![Federação](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")  
  
## <a name="summary"></a>Resumo  
 Segurança federada fornece uma divisão limpa de responsabilidade e ajuda a criar arquiteturas de serviço segura e escalonável. Como uma plataforma para criar e implantar aplicativos distribuídos, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece suporte nativo para implementar segurança federada.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
