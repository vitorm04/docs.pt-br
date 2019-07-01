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
ms.openlocfilehash: 295e4bd5eca58bc190b31fd96e79f97678e381a4
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486780"
---
# <a name="federation"></a>Federação
Este tópico fornece uma visão geral do conceito de segurança federada. Ele também descreve o suporte do Windows Communication Foundation (WCF) para implantação de arquiteturas de segurança federada. Para um aplicativo de exemplo que demonstra a federação, consulte [exemplo de Federação](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definição da segurança federada  
 Segurança federada permite uma separação clara entre o serviço de que um cliente está acessando e os procedimentos de autenticação e autorização associados. Segurança federada também permite a colaboração em vários sistemas, redes e as organizações em territórios diferentes de confiança.  
  
 O WCF oferece suporte para criação e implantação de sistemas distribuídos que emprega segurança federada.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Elementos de uma arquitetura de segurança federada  
 A arquitetura de segurança federada tem três elementos principais, conforme descrito na tabela a seguir.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Realm/domínio|Uma única unidade de administração de segurança ou confiabilidade. Um domínio típico pode incluir uma única organização.|  
|Federação|Uma coleção de domínios que tenham estabelecido confiança. O nível de confiança pode variar, mas normalmente inclui autenticação e quase sempre inclui a autorização. Uma federação típica pode incluir um número de organizações que tenham estabelecido de confiança para acesso compartilhado a um conjunto de recursos.|  
|STS (Serviço de Token de Segurança)|Um serviço Web que emite tokens de segurança; ou seja, ele faz declarações com base na evidência de que ele confia, para qualquer pessoa que confia nele. Isso constitui a base de intermediar a confiança entre domínios.|  
  
### <a name="example-scenario"></a>Cenário de exemplo  
 A ilustração a seguir mostra um exemplo de segurança federada:  
  
 ![Diagrama mostrando um cenário típico de segurança federada.](./media/federation/typical-federated-security-scenario.gif)  
  
 Este cenário inclui duas organizações: A e B. organização B tem um recurso da Web (um serviço da Web) que alguns usuários em uma organização consideram valiosos.  
  
> [!NOTE]
>  Esta seção usa os termos *resource*, *service*, e *serviço Web* alternadamente.  
  
 Normalmente, a organização B requer que um usuário de uma organização a fornecer alguma forma válida de autenticação antes de acessar o serviço. Além disso, a organização também pode exigir que o usuário seja autorizado a acessar o recurso específico em questão. Uma maneira de resolver esse problema e permitir que os usuários na organização A acessar o recurso na organização B é da seguinte maneira:  
  
- Os usuários de uma organização a registrar suas credenciais (um nome de usuário e senha) a organização B.  
  
- Durante o acesso aos recursos, os usuários de uma organização a apresentam suas credenciais para a organização B e são autenticados antes de acessar o recurso.  
  
 Essa abordagem tem três desvantagens significativas:  
  
- Organização B deve gerenciar as credenciais para usuários de uma organização, além de gerenciar as credenciais de seus usuários locais.  
  
- Os usuários em uma organização precisam manter um conjunto adicional de credenciais (ou seja, lembre-se um nome adicional do usuário e senha) além das credenciais que normalmente usam para obter acesso aos recursos dentro da organização A. Geralmente, isso incentiva a prática de usar o mesmo nome de usuário e senha em vários sites de serviço, que é uma medida de segurança fraca.  
  
- A arquitetura não é dimensionado à medida que mais organizações percebem o recurso na organização B como sendo de algum valor.  
  
 Uma abordagem alternativa, que trata das desvantagens mencionadas anteriormente, é empregar segurança federada. Nessa abordagem, as organizações A e B estabelecer uma relação de confiança em empregam o serviço de Token de segurança (STS) para habilitar o agente da relação de confiança estabelecida.  
  
 Em uma arquitetura de segurança federada, a usuários de uma organização sabem que se eles desejam acessar o serviço Web na organização B que eles devem apresentar um token de segurança válido do STS na organização B, que autentica e autoriza o acesso à serviço específico.  
  
 Em entrar em contato com o STS B, os usuários recebem a outro nível de indireção da política associada com o STS. Eles devem apresentar uma segurança válido token da STS A (ou seja, o realm da relação de confiança do cliente) antes de B o STS pode emitir a eles um token de segurança. Este é um corolário da relação de confiança estabelecida entre as duas organizações e implica que organização B não precisa gerenciar as identidades dos usuários da organização A. Na prática, o STS B normalmente tem um valor nulo `issuerAddress` e `issuerMetadataAddress`. Para obter mais informações, confira [Como: Configurar um emissor Local](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). Nesse caso, o cliente consulta uma diretiva local para localizar o STS A. Essa configuração é chamada *federação realm de início* e dimensiona melhor porque não tem STS B manter informações sobre STS A.  
  
 Os usuários, em seguida, entre em contato com o STS em uma organização e obter um token de segurança, apresentando credenciais de autenticação que normalmente usam para obter acesso a qualquer outro recurso dentro da organização A. Isso também reduz o problema de usuários precisar manter vários conjuntos de credenciais ou usando o mesmo conjunto de credenciais em vários sites de serviço.  
  
 Depois que os usuários obter um token de segurança da STS A, eles apresentam o token para o STS B. esta organização continua a executar a autorização de solicitações de usuários e emite um token de segurança para os usuários do seu próprio conjunto de tokens de segurança. Os usuários, em seguida, podem apresentar seu token para o recurso na organização B e acessar o serviço.  
  
## <a name="support-for-federated-security-in-wcf"></a>Suporte para segurança federada no WCF  
 O WCF fornece suporte turnkey para implantação de arquiteturas de segurança federada por meio de [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 O [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elemento fornece para uma associação segura, confiável e interoperável que envolve o uso de HTTP como o mecanismo de transporte subjacente para o estilo de comunicação de solicitação-resposta, empregar o texto e XML como formato de conexão para a codificação.  
  
 O uso de [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) em uma segurança federada cenário pode ser desacoplado em duas fases logicamente independentes, conforme descrito nas seções a seguir.  
  
### <a name="phase-1-design-phase"></a>Fase 1: Fase de design  
 Durante a fase de design, o cliente usa o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para ler a política que expõe o ponto de extremidade de serviço e para coletar os requisitos de autenticação e autorização do serviço. Os proxies apropriados são construídos para criar o seguinte padrão de comunicação de segurança federada no cliente:  
  
- Obter um token de segurança do STS no território de confiança do cliente.  
  
- Apresente o token para o STS no território de confiança do serviço.  
  
- Obter um token de segurança do STS no território de confiança do serviço.  
  
- Apresente o token para o serviço para acessar o serviço.  
  
### <a name="phase-2-run-time-phase"></a>Fase 2: Fase de tempo de execução  
 Durante a fase de tempo de execução, o cliente cria uma instância de um objeto da classe de cliente WCF e faz uma chamada usando o cliente do WCF. A estrutura subjacente do WCF manipula as etapas mencionadas anteriormente o padrão de comunicação de segurança federada e permite que o cliente consumir diretamente o serviço.  
  
## <a name="sample-implementation-using-wcf"></a>Implementação de exemplo usando o WCF  
 A ilustração a seguir mostra uma implementação de exemplo para uma arquitetura de segurança federada usando o suporte nativo do WCF.  
  
 ![Diagrama que mostra um exemplo de implementação de segurança de Federação.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Exemplo MyService  
 O serviço `MyService` expõe um ponto de extremidade por meio de `MyServiceEndpoint`. A ilustração a seguir mostra o endereço, ligação e contrato associado com o ponto de extremidade.  
  
 ![Diagrama mostrando os detalhes de MyServiceEndpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 O ponto de extremidade de serviço `MyServiceEndpoint` usa o [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e requer um token válido de asserções marcação linguagem SAML (Security) com um `accessAuthorized` declaração emitida pelo STS B. Isso é especificado declarativamente na configuração do serviço.  
  
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
>  Um ponto sutil deve ser observado sobre as declarações necessárias para `MyService`. A segunda Figura indica que `MyService` requer um token SAML com o `accessAuthorized` de declaração. Para ser mais preciso, isso Especifica a declaração de tipo que `MyService` requer. O nome totalmente qualificado desse tipo de declaração é `http://tempuri.org:accessAuthorized` (juntamente com o namespace associado), que é usado no arquivo de configuração de serviço. O valor dessa declaração indica a presença da declaração e deve ser definido como `true` pelo STS B.  
  
 Em tempo de execução, essa política é imposta pelo `MyServiceOperationRequirement` que é implementado como parte da classe a `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 A ilustração a seguir mostra o STS B. Conforme mencionado anteriormente, um serviço de token de segurança (STS) também é um serviço Web e pode ter seus pontos de extremidade associados, política e assim por diante.  
  
 ![Diagrama mostrando o serviço de token de segurança B.](./media/federation/myservice-security-token-service-b.gif)  
  
 STS B expõe um ponto de extremidade, chamado `STSEndpoint` que podem ser usadas para solicitar tokens de segurança. Especificamente, STS B emite tokens SAML com o `accessAuthorized` de declaração, que pode ser apresentado na `MyService` site de serviço para acessar o serviço. No entanto, o STS B exige que os usuários apresentar um token SAML válido emitido pelo STS A que contém o `userAuthenticated` de declaração. Isso é especificado declarativamente na configuração de STS.  
  
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
>  Novamente, o `userAuthenticated` declaração é o tipo de declaração que é exigido pelo STS B. O nome totalmente qualificado desse tipo de declaração é `http://tempuri.org:userAuthenticated` (juntamente com o namespace associado), que é usado no arquivo de configuração de STS. O valor dessa declaração indica a presença da declaração e deve ser definido como `true` pelo STS A.  
  
 Em tempo de execução, o `STS_B_OperationRequirement` classe impõe essa política, o que é implementada como parte do STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Se a verificação de acesso estiver desmarcada, STS B emite um token SAML com o `accessAuthorized` de declaração.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 A ilustração a seguir mostra o STS A.  
  
 ![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Semelhante do STS B, ao STS também é um serviço Web que emite tokens de segurança e expõe um ponto de extremidade para essa finalidade. No entanto, ele usa uma ligação diferente (`wsHttpBinding`) e requer que os usuários apresentem um CardSpace válido com um `emailAddress` de declaração. Em resposta, ele emite tokens SAML com o `userAuthenticated` de declaração. Isso é especificado declarativamente na configuração do serviço.  
  
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
  
 Em tempo de execução, o `STS_A_OperationRequirement` classe impõe essa política, o que é implementada como parte do STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Se o acesso for `true`, STS A emite um token SAML com `userAuthenticated` de declaração.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Cliente em uma organização  
 A ilustração a seguir mostra o cliente em uma organização, juntamente com as etapas envolvidas na tomada de uma `MyService` chamada de serviço. Os outros componentes funcionais também estão incluídos para fins de integridade.  
  
 ![Diagrama mostrando as etapas em uma chamada de serviço MyService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Resumo  
 Segurança federada fornece uma divisão limpa de responsabilidade e ajuda a compilar arquiteturas de serviço seguro e escalonável. Como uma plataforma para criar e implantar aplicativos distribuídos, o WCF fornece suporte nativo para a implementação de segurança federada.  
  
## <a name="see-also"></a>Consulte também

- [Segurança](../../../../docs/framework/wcf/feature-details/security.md)
