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
ms.openlocfilehash: 86c679af77f2b7b1960e7489e0e6e61b811e1bad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185219"
---
# <a name="federation"></a>Federação
Este tópico fornece uma breve visão geral do conceito de segurança federada. Ele também descreve o suporte da Windows Communication Foundation (WCF) para implantar arquiteturas de segurança federadas. Para obter uma aplicação de amostra que demonstre federação, consulte [Amostra de Federação](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definição de Segurança Federada  
 A segurança federada permite uma separação limpa entre o serviço que um cliente está acessando e os procedimentos de autenticação e autorização associados. A segurança federada também permite a colaboração entre vários sistemas, redes e organizações em diferentes áreas de confiança.  
  
 O WCF fornece suporte para a construção e implantação de sistemas distribuídos que empregam segurança federada.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Elementos de uma arquitetura de segurança federada  
 A arquitetura de segurança federada tem três elementos-chave, conforme descrito na tabela a seguir.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Domínio/reino|Uma única unidade de administração de segurança ou confiança. Um domínio típico pode incluir uma única organização.|  
|Federação|Uma coleção de domínios que estabeleceram confiança. O nível de confiança pode variar, mas normalmente inclui a autenticação e quase sempre inclui a autorização. Uma federação típica pode incluir um número de organizações que estabeleceram confiança para acesso compartilhado a um conjunto de recursos.|  
|STS (Serviço de Token de Segurança)|Um serviço web que emite tokens de segurança; ou seja, faz afirmações baseadas em evidências em que confia, a quem confia nele. Isso forma a base da intermediação de confiança entre domínios.|  
  
### <a name="example-scenario"></a>Cenário de Exemplo  
 A ilustração a seguir mostra um exemplo de segurança federada:  
  
 ![Diagrama mostrando um típico cenário de segurança federada.](./media/federation/typical-federated-security-scenario.gif)  
  
 Este cenário inclui duas organizações: A e B. A Organization B tem um recurso web (um serviço web) que alguns usuários da organização A acham valioso.  
  
> [!NOTE]
> Esta seção usa os termos *recurso,* *serviço*e *serviço web* intercambiavelmente.  
  
 Normalmente, a organização B exige que um usuário da organização A forneça alguma forma válida de autenticação antes de acessar o serviço. Além disso, a organização também pode exigir que o usuário seja autorizado a acessar o recurso específico em questão. Uma maneira de resolver esse problema e permitir que os usuários da organização A acessem o recurso na organização B é a seguinte:  
  
- Usuários da organização A registram suas credenciais (nome de usuário e senha) com a organização B.  
  
- Durante o acesso aos recursos, os usuários da organização A apresentam suas credenciais à organização B e são autenticados antes de acessar o recurso.  
  
 Esta abordagem tem três desvantagens significativas:  
  
- A organização B tem que gerenciar as credenciais para usuários da organização A, além de gerenciar as credenciais de seus usuários locais.  
  
- Usuários na organização A precisam manter um conjunto adicional de credenciais (ou seja, lembre-se de um nome de usuário e senha adicionais) além das credenciais que normalmente usam para obter acesso aos recursos dentro da organização A. Isso geralmente incentiva a prática de usar o mesmo nome de usuário e senha em vários sites de serviço, o que é uma medida de segurança fraca.  
  
- A arquitetura não é dimensionada à medida que mais organizações percebem o recurso na organização B como sendo de algum valor.  
  
 Uma abordagem alternativa, que aborda as desvantagens mencionadas anteriormente, é empregar segurança federada. Nessa abordagem, as organizações A e B estabelecem um relacionamento de confiança e empregam o Security Token Service (STS) para permitir a intermediação da confiança estabelecida.  
  
 Em uma arquitetura de segurança federada, os usuários da organização A sabem que, se quiserem acessar o serviço Web na organização B, devem apresentar um token de segurança válido do STS na organização B, que autentica e autoriza seu acesso ao serviço específico.  
  
 Ao entrar em contato com o STS B, os usuários recebem outro nível de indireção da política associada ao STS. Eles devem apresentar um token de segurança válido do STS A (ou seja, o reino da confiança do cliente) antes que o STS B possa emitir-lhes um token de segurança. Este é um corolário da relação de confiança estabelecida entre as duas organizações e implica que a organização B não precisa gerenciar identidades para usuários da organização A. Na prática, o STS B `issuerAddress` `issuerMetadataAddress`normalmente tem um nulo e . Para obter mais informações, [consulte Como: Configurar um emissor local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). Nesse caso, o cliente consulta uma política local para localizar o STS A. Essa configuração é chamada *de federação de reino doméstico* e ela é melhor porque o STS B não precisa manter informações sobre o STS A.  
  
 Em seguida, os usuários entram em contato com o STS na organização A e obtêm um token de segurança apresentando credenciais de autenticação que normalmente usam para obter acesso a qualquer outro recurso dentro da organização A. Isso também alivia o problema de os usuários terem que manter vários conjuntos de credenciais ou usar o mesmo conjunto de credenciais em vários sites de serviço.  
  
 Uma vez que os usuários obtenham um token de segurança do STS A, eles apresentam o token para o STS B. A Organização B passa a realizar a autorização das solicitações dos usuários e emite um token de segurança para os usuários a partir de seu próprio conjunto de tokens de segurança. Os usuários podem então apresentar seu token ao recurso na organização B e acessar o serviço.  
  
## <a name="support-for-federated-security-in-wcf"></a>Apoio à Segurança Federada no WCF  
 O WCF oferece suporte por turno para implantar arquiteturas de segurança federadas através do [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 O elemento [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) fornece uma vinculação segura, confiável e interoperável que implica o uso do HTTP como mecanismo de transporte subjacente ao estilo de comunicação solicitação-resposta, empregando texto e XML como o formato de fio para codificação.  
  
 O uso de [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) em um cenário de segurança federada pode ser dissociado em duas fases logicamente independentes, conforme descrito nas seções a seguir.  
  
### <a name="phase-1-design-phase"></a>Fase 1: Fase de Design  
 Durante a fase de projeto, o cliente usa a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para ler a política que o ponto final do serviço expõe e coletar os requisitos de autenticação e autorização do serviço. Os proxies apropriados são construídos para criar o seguinte padrão de comunicação de segurança federada no cliente:  
  
- Obtenha um token de segurança do STS no reino da confiança do cliente.  
  
- Apresente o token ao STS no reino da confiança de serviço.  
  
- Obtenha um token de segurança do STS no reino do fundo de serviço.  
  
- Apresentar o token ao serviço para acessar o serviço.  
  
### <a name="phase-2-run-time-phase"></a>Fase 2: Fase de tempo de execução  
 Durante a fase de tempo de execução, o cliente instancia um objeto da classe cliente WCF e faz uma chamada usando o cliente WCF. O quadro subjacente do WCF lida com as etapas mencionadas anteriormente no padrão de comunicação de segurança federada e permite que o cliente consuma perfeitamente o serviço.  
  
## <a name="sample-implementation-using-wcf"></a>Implementação de amostras usando WCF  
 A ilustração a seguir mostra uma implementação de amostra para uma arquitetura de segurança federada usando o suporte nativo do WCF.  
  
 ![Diagrama mostrando uma amostra de implementação de segurança da Federação.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Exemplo MyService  
 O `MyService` serviço expõe um único `MyServiceEndpoint`ponto final através de . A ilustração a seguir mostra o endereço, vinculação e contrato associados ao ponto final.  
  
 ![Diagrama mostrando os detalhes do MyServiceEndpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 O ponto `MyServiceEndpoint` final do serviço usa o [ \<>wsFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e requer um token `accessAuthorized` saml (Security Assertions Markup Language, linguagem de marcação de afirmações de segurança) válido com uma reclamação emitida pelo STS B. Isso é declarativamente especificado na configuração do serviço.  
  
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
> Um ponto sutil deve ser observado `MyService`sobre as reivindicações exigidas por . A segunda figura `MyService` indica que requer um `accessAuthorized` token SAML com a reclamação. Para ser mais preciso, isso especifica `MyService` o tipo de reclamação que requer. O nome totalmente qualificado deste `http://tempuri.org:accessAuthorized` tipo de reclamação é (juntamente com o namespace associado), que é usado no arquivo de configuração de serviço. O valor desta reivindicação indica a presença desta reivindicação `true` e é assumido como definido pela STS B.  
  
 Em tempo de execução, esta `MyServiceOperationRequirement` política é aplicada pela `MyService`classe que é implementada como parte do .  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 A ilustração a seguir mostra o STS B. Como dito anteriormente, um serviço de token de segurança (STS) também é um serviço da Web e pode ter seus pontos finais associados, política e assim por diante.  
  
 ![Diagrama mostrando o serviço de token de segurança B.](./media/federation/myservice-security-token-service-b.gif)  
  
 O STS B expõe um `STSEndpoint` único ponto final, chamado que pode ser usado para solicitar tokens de segurança. Especificamente, o STS B emite tokens SAML com a `accessAuthorized` reclamação, que podem ser apresentados no site do `MyService` serviço para acessar o serviço. No entanto, o STS B exige que os usuários apresentem `userAuthenticated` um token SAML válido emitido pelo STS A que contenha a reivindicação. Isso é declarativamente especificado na configuração STS.  
  
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
> Novamente, `userAuthenticated` a reivindicação é o tipo de sinistro que é exigido pelo STS B. O nome totalmente qualificado deste `http://tempuri.org:userAuthenticated` tipo de reivindicação é (juntamente com o namespace associado), que é usado no arquivo de configuração STS. O valor desta reivindicação indica a presença desta reivindicação `true` e é assumido como sendo definido pela STS A.  
  
 Em tempo de `STS_B_OperationRequirement` execução, a classe impõe essa política, que é implementada como parte da STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Se a verificação de acesso estiver clara, o STS `accessAuthorized` B emitirá um token SAML com a reclamação.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 A ilustração a seguir mostra o STS A.  
  
 ![Federação](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Semelhante ao STS B, o STS A também é um serviço web que emite tokens de segurança e expõe um único ponto final para este fim. No entanto, ele`wsHttpBinding`usa uma vinculação diferente ( ) `emailAddress` e exige que os usuários apresentem um CardSpace válido com uma reclamação. Em resposta, ele emite tokens `userAuthenticated` SAML com a reivindicação. Isso é declarativamente especificado na configuração do serviço.  
  
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
  
 Em tempo de `STS_A_OperationRequirement` execução, a classe impõe essa política, que é implementada como parte da STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Se o `true`acesso for , STS A emitirá `userAuthenticated` um token SAML com reclamação.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Cliente na Organização A  
 A ilustração a seguir mostra o cliente na organização `MyService` A, juntamente com as etapas envolvidas na realização de uma chamada de serviço. Os outros componentes funcionais também estão incluídos para completude.  
  
 ![Diagrama mostrando as etapas em uma chamada de serviço do MyService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Resumo  
 A segurança federada fornece uma divisão limpa de responsabilidade e ajuda a construir arquiteturas de serviços seguras e escaláveis. Como uma plataforma para construir e implantar aplicativos distribuídos, o WCF fornece suporte nativo para implementar a segurança federada.  
  
## <a name="see-also"></a>Confira também

- [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
