---
title: Delegação e representação com o WCF
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
- impersonation [WCF]
- delegation [WCF]
ms.assetid: 110e60f7-5b03-4b69-b667-31721b8e3152
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 885faab43b620cf347c1780d445a72361cb5cdb4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="delegation-and-impersonation-with-wcf"></a>Delegação e representação com o WCF
*Representação* é uma técnica comum que os serviços usam para restringir o acesso de cliente aos recursos de um domínio serviço. Recursos de domínio de serviço podem ser recursos do computador, como arquivos locais (representação), ou um recurso em outro computador, como um compartilhamento de arquivo (delegação). Para um aplicativo de exemplo, consulte [representar o cliente](../../../../docs/framework/wcf/samples/impersonating-the-client.md). Para obter um exemplo de como usar a representação, consulte [como: representar um cliente em um serviço](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md).  
  
> [!IMPORTANT]
>  Lembre-se de que, ao representar um cliente em um serviço, o serviço é executado com as credenciais do cliente, que podem ter mais privilégios que o processo do servidor.  
  
## <a name="overview"></a>Visão geral  
 Normalmente, os clientes chamar um serviço para que o serviço executar alguma ação no nome do cliente. A representação permite que o serviço atuar como o cliente ao executar a ação. A delegação permite que um serviço front-end encaminhar a solicitação do cliente para um serviço de back-end de forma que o serviço de back-end também pode representar o cliente. Geralmente, a representação é usada como uma maneira de verificar se um cliente está autorizado a executar uma ação específica, enquanto a delegação é uma maneira de fluxo de recursos de representação, junto com a identidade do cliente, para um serviço back-end. A delegação é um recurso do domínio Windows que pode ser usado quando a autenticação Kerberos é executada. A delegação é diferente do fluxo de identidade e, como a delegação transfere a capacidade de representar o cliente sem posse da senha do cliente, é uma quantidade maior operação privilegiada de fluxo de identidade.  
  
 Representação e delegação exigem que o cliente tenha uma identidade do Windows. Se um cliente não possui uma identidade do Windows, a única opção disponível é a identidade do cliente para o segundo serviço de fluxo.  
  
## <a name="impersonation-basics"></a>Noções básicas de representação  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dá suporte à representação para uma variedade de credenciais de cliente. Este tópico descreve o suporte de modelo de serviço para representar o chamador durante a implementação de um método de serviço. Também são abordadas cenários comuns de implantação que envolve a representação e segurança de SOAP e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] opções nesses cenários.  
  
 Este tópico enfoca a representação e delegação em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ao usar a segurança SOAP. Você também pode usar a representação e delegação com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ao usar a segurança de transporte, conforme descrito em [usando representação com segurança de transporte](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md).  
  
## <a name="two-methods"></a>Dois métodos  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Segurança SOAP tem dois métodos distintos para executar representação. O método usado depende da associação. Uma é a representação de um token do Windows obtido com a autenticação Kerberos ou de Interface de provedor de suporte de segurança (SSPI), que é armazenado em cache, em seguida, no serviço. A segunda é a representação de um token do Windows obtido extensões Kerberos, coletivamente chamadas *Service-for-User* (S4U).  
  
### <a name="cached-token-impersonation"></a>Representação de Token em cache  
 Você pode executar a representação de token armazenado em cache com o seguinte:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, e <xref:System.ServiceModel.NetTcpBinding> com uma credencial de cliente do Windows.  
  
-   <xref:System.ServiceModel.BasicHttpBinding> com um <xref:System.ServiceModel.BasicHttpSecurityMode> definido como o <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> credencial ou qualquer outra associação padrão em que o cliente apresenta uma credencial de nome de usuário que o serviço pode ser mapeados para uma conta válida do Windows.  
  
-   Qualquer <xref:System.ServiceModel.Channels.CustomBinding> que usa uma credencial de cliente do Windows com o `requireCancellation` definido como `true`. (A propriedade está disponível nas seguintes classes: <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>, <xref:System.ServiceModel.Security.Tokens.SslSecurityTokenParameters>, e <xref:System.ServiceModel.Security.Tokens.SspiSecurityTokenParameters>.) Se uma conversa segura é usada na associação, ela também deve ter o `requireCancellation` propriedade definida como `true`.  
  
-   Qualquer <xref:System.ServiceModel.Channels.CustomBinding> onde o cliente apresenta uma credencial de nome de usuário. Se a conversa segura é usada na associação, ela também deve ter o `requireCancellation` propriedade definida como `true`.  
  
### <a name="s4u-based-impersonation"></a>Representação S4U com base em  
 Você pode executar com base em S4U representação com o seguinte:  
  
-   <xref:System.ServiceModel.WSHttpBinding>, <xref:System.ServiceModel.WSDualHttpBinding>, e <xref:System.ServiceModel.NetTcpBinding> com uma credencial de cliente de certificado que o serviço pode ser mapeados para uma conta válida do Windows.  
  
-   Qualquer <xref:System.ServiceModel.Channels.CustomBinding> que usa uma credencial de cliente do Windows com o `requireCancellation` propriedade definida como `false`.  
  
-   Qualquer <xref:System.ServiceModel.Channels.CustomBinding> que usa um nome de usuário ou a credencial de cliente do Windows e a conversa segura com o `requireCancellation` propriedade definida como `false`.  
  
 A extensão à qual o serviço pode representar o cliente depende dos privilégios que a conta de serviço mantém quando ele tenta representação, o tipo de representação usada e possivelmente a extensão de representação que permite que o cliente.  
  
> [!NOTE]
>  Quando o cliente e o serviço estiverem em execução no mesmo computador e o cliente é executado sob uma conta de sistema (por exemplo, `Local System` ou `Network Service`), o cliente não pode ser representado quando uma sessão segura é estabelecida com o contexto de segurança com monitoração de estado tokens. Um aplicativo Windows Form ou console normalmente é executado sob a conta conectado no momento, para que a conta pode ser representada por padrão. No entanto, quando o cliente é um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] página e que é hospedado no [!INCLUDE[iis601](../../../../includes/iis601-md.md)] ou [!INCLUDE[iisver](../../../../includes/iisver-md.md)], em seguida, execute o cliente no `Network Service` por padrão. Todas as associações fornecidas pelo sistema que oferecem suporte a sessões seguras usam um token de contexto de segurança sem monitoração de estado (SCT) por padrão. No entanto, se o cliente é um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] página e sessões seguras com monitoração de estado SCTs forem usados, o cliente não pode ser representado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] usando SCTs com monitoração de estado em uma sessão segura, consulte [como: criar um Token de contexto de segurança para uma sessão segura](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
## <a name="impersonation-in-a-service-method-declarative-model"></a>Representação em um método de serviço: modelo declarativo  
 A maioria dos cenários de representação envolvem a execução do método de serviço no contexto do chamador. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Fornece um recurso de representação que torna isso fácil de fazer, permitindo que o usuário especifique o requisito de representação no <xref:System.ServiceModel.OperationBehaviorAttribute> atributo. Por exemplo, no código a seguir, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura representará o chamador antes de executar o `Hello` método. Qualquer tentativa de acessar recursos nativos dentro de `Hello` método só terá êxito se a lista de controle de acesso (ACL) do recurso permite que o chamador de privilégios de acesso. Para habilitar a representação, defina o <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> propriedade para um do <xref:System.ServiceModel.ImpersonationOption> valores de enumeração, ou <xref:System.ServiceModel.ImpersonationOption.Required?displayProperty=nameWithType> ou <xref:System.ServiceModel.ImpersonationOption.Allowed?displayProperty=nameWithType>, conforme mostrado no exemplo a seguir.  
  
> [!NOTE]
>  Quando um serviço possui credenciais mais alto que o cliente remoto, as credenciais do serviço são usadas se o <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> está definida como <xref:System.ServiceModel.ImpersonationOption.Allowed>. Ou seja, se um usuário de baixo privilégio fornecer suas credenciais, um serviço de privilégios mais altos executa o método com as credenciais do serviço e pode usar recursos que o usuário de baixo privilégio caso contrário, não seria capaz de usar.  
  
 [!code-csharp[c_ImpersonationAndDelegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#1)]
 [!code-vb[c_ImpersonationAndDelegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#1)]  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura pode representar o chamador somente se o chamador é autenticado com as credenciais que podem ser mapeadas para uma conta de usuário do Windows. Se o serviço está configurado para se autenticar usando uma credencial que não pode ser mapeada para uma conta do Windows, o método de serviço não será executado.  
  
> [!NOTE]
>  Em [!INCLUDE[wxp](../../../../includes/wxp-md.md)], representação falhará se um stateful SCT é criado, resultando em um <xref:System.InvalidOperationException>. Para obter mais informações, consulte [cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="impersonation-in-a-service-method-imperative-model"></a>Representação em um método de serviço: modelo obrigatório  
 Às vezes, um chamador não precisa representar o método de todo o serviço de função, mas para apenas uma parte dele. Nesse caso, obtenha a identidade do Windows do chamador dentro do método de serviço e executar imperativa a representação. Fazer isso usando o <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> propriedade o <xref:System.ServiceModel.ServiceSecurityContext> para retornar uma instância do <xref:System.Security.Principal.WindowsIdentity> classe e chamar o <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> método antes de usar a instância.  
  
> [!NOTE]
>  Certifique-se de usar o Visual Basic`Using` instrução ou c# `using` instrução automaticamente reverter a ação de representação. Se você não usar a instrução, ou se você usar uma linguagem de programação que não seja do Visual Basic ou c#, certifique-se de reverter o nível de representação. Falha ao fazer isso pode formar a base para a negação de serviço e elevação de ataques de privilégio.  
  
 [!code-csharp[c_ImpersonationAndDelegation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#2)]
 [!code-vb[c_ImpersonationAndDelegation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#2)]  
  
## <a name="impersonation-for-all-service-methods"></a>Representação de todos os métodos de serviço  
 Em alguns casos, você deve executar todos os métodos de um serviço no contexto do chamador. Em vez de explicitamente habilitar esse recurso em uma base por método, use o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Conforme mostrado no código a seguir, defina o <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A> propriedade `true`. O <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> são recuperados das coleções de comportamentos do <xref:System.ServiceModel.ServiceHost> classe. Observe também que o `Impersonation` propriedade o <xref:System.ServiceModel.OperationBehaviorAttribute> aplicado para cada método também deve ser definido como <xref:System.ServiceModel.ImpersonationOption.Allowed> ou <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
 [!code-csharp[c_ImpersonationAndDelegation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#3)]
 [!code-vb[c_ImpersonationAndDelegation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#3)]  
  
 A tabela a seguir descreve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comportamento para todas as combinações possíveis de `ImpersonationOption` e `ImpersonateCallerForAllServiceOperations`.  
  
|`ImpersonationOption`|`ImpersonateCallerForAllServiceOperations`|Comportamento|  
|---------------------------|------------------------------------------------|--------------|  
|Necessária|N/D|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] representa o chamador|  
|Permitido|false|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não representar o chamador|  
|Permitido|true|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] representa o chamador|  
|Não permitido|false|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não representar o chamador|  
|Não permitido|true|Não permitido. (Um <xref:System.InvalidOperationException> é gerada.)|  
  
## <a name="impersonation-level-obtained-from-windows-credentials-and-cached-token-impersonation"></a>Nível de representação obtidas as credenciais do Windows e armazenado em cache o Token de representação  
 Em alguns cenários, o cliente tem parcial controle sobre o nível de representação que o serviço executa quando uma credencial de cliente do Windows é usada. Um cenário ocorre quando o cliente especifica um nível de representação anônima. O outro ocorre ao executar a representação com um token de cache. Isso é feito definindo o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> propriedade o <xref:System.ServiceModel.Security.WindowsClientCredential> classe, que pode é acessada como uma propriedade de genérica <xref:System.ServiceModel.ChannelFactory%601> classe.  
  
> [!NOTE]
>  Especificar um nível de representação de Anonymous faz com que o cliente fazer logon serviço anonimamente. O serviço, portanto, deve permitir logons anônimos, independentemente se a representação é executada.  
  
 O cliente pode especificar o nível de representação como <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, <xref:System.Security.Principal.TokenImpersonationLevel.Identification>, <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, ou <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. Apenas um token no nível especificado é produzido, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_ImpersonationAndDelegation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_impersonationanddelegation/cs/source.cs#4)]
 [!code-vb[c_ImpersonationAndDelegation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_impersonationanddelegation/vb/source.vb#4)]  
  
 A tabela a seguir especifica o nível de representação que o serviço obtém a representação de um token em cache.  
  
|Valor `AllowedImpersonationLevel`|Serviço tem `SeImpersonatePrivilege`|Cliente e serviço são capazes de delegação|Token de cache `ImpersonationLevel`|  
|---------------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Anônimo|Sim|N/D|Representação|  
|Anônimo|Não|N/D|Identificação|  
|Identificação|N/D|N/D|Identificação|  
|Representação|Sim|N/D|Representação|  
|Representação|Não|N/D|Identificação|  
|Delegação|Sim|Sim|Delegação|  
|Delegação|Sim|Não|Representação|  
|Delegação|Não|N/D|Identificação|  
  
## <a name="impersonation-level-obtained-from-user-name-credentials-and-cached-token-impersonation"></a>Nível de representação obtidos de credenciais de nome de usuário e armazenados em cache o Token de representação  
 Passando o serviço de seu nome de usuário e senha, permite que um cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para fazer logon como esse usuário, que é equivalente à configuração de `AllowedImpersonationLevel` propriedade <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>. (O `AllowedImpersonationLevel` está disponível na <xref:System.ServiceModel.Security.WindowsClientCredential> e <xref:System.ServiceModel.Security.HttpDigestClientCredential> classes.) A tabela a seguir fornece a representação de nível obtida quando o serviço recebe as credenciais de nome de usuário.  
  
|`AllowedImpersonationLevel`|Serviço tem `SeImpersonatePrivilege`|Cliente e serviço são capazes de delegação|Token de cache `ImpersonationLevel`|  
|---------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|N/D|Sim|Sim|Delegação|  
|N/D|Sim|Não|Representação|  
|N/D|Não|N/D|Identificação|  
  
## <a name="impersonation-level-obtained-from-s4u-based-impersonation"></a>Obtido com base em S4U representação de nível de representação  
  
|Serviço tem `SeTcbPrivilege`|Serviço tem `SeImpersonatePrivilege`|Cliente e serviço são capazes de delegação|Token de cache `ImpersonationLevel`|  
|----------------------------------|------------------------------------------|--------------------------------------------------|---------------------------------------|  
|Sim|Sim|N/D|Representação|  
|Sim|Não|N/D|Identificação|  
|Não|N/D|N/D|Identificação|  
  
## <a name="mapping-a-client-certificate-to-a-windows-account"></a>Mapeamento de um certificado de cliente para uma conta do Windows  
 É possível que um cliente para autenticar-se a um serviço usando um certificado e tem o mapa de serviço de cliente para uma conta existente por meio do Active Directory. O XML a seguir mostra como configurar o serviço para mapear o certificado.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="MapToWindowsAccount">  
      <serviceCredentials>  
        <clientCertificate>  
          <authentication mapClientCertificateToWindowsAccount="true" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 O código a seguir mostra como configurar o serviço.  
  
```  
// Create a binding that sets a certificate as the client credential type.  
WSHttpBinding b = new WSHttpBinding();  
b.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a service host that maps the certificate to a Windows account.  
Uri httpUri = new Uri("http://localhost/Calculator");  
ServiceHost sh = new ServiceHost(typeof(HelloService), httpUri);  
sh.Credentials.ClientCertificate.Authentication.MapClientCertificateToWindowsAccount = true;  
```  
  
## <a name="delegation"></a>Delegação  
 Para delegar a um serviço de back-end, um serviço deve executar o multi-trecho de Kerberos (SSPI sem o fallback de NTLM) ou Kerberos direto de autenticação para o serviço de back-end usando a identidade do cliente Windows. Para delegar a um serviço de back-end, crie um <xref:System.ServiceModel.ChannelFactory%601> e um canal e se comunicar por meio do canal ao representar o cliente. Com essa forma de delegação, a distância em que o serviço de back-end pode ser localizado do serviço de front-end depende do nível de representação obtido com o serviço de front-end. Quando o nível de representação é <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>, os serviços de front-end e back-end devem ser executados no mesmo computador. Quando o nível de representação é <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, os serviços de front-end e back-end podem ser em computadores separados ou no mesmo computador. Habilitando a representação de nível de delegação exige a configuração de diretiva de domínio do Windows para permitir a delegação. Para obter mais informações sobre como configurar o Active Directory para suporte à delegação, consulte [habilitando a autenticação delegada](http://go.microsoft.com/fwlink/?LinkId=99690).  
  
> [!NOTE]
>  Quando um cliente é autenticado para o serviço de front-end usando um nome de usuário e senha que correspondem a uma conta do Windows no serviço de back-end, o serviço de front-end pode autenticar para o serviço de back-end com a reutilização de nome de usuário e a senha do cliente. Esta é uma forma muito eficiente de fluxo de identidade, como passando o nome de usuário e senha para o serviço de back-end permite que o serviço de back-end executar representação, mas não constitui a delegação porque Kerberos não é usado. Controles de Active Directory sobre a delegação não se aplicam à autenticação de nome e a senha do usuário.  
  
### <a name="delegation-ability-as-a-function-of-impersonation-level"></a>Capacidade de delegação como uma função de nível de representação  
  
|Nível de representação|O serviço pode executar processo cruzado de delegação|O serviço pode executar delegação entre computadores|  
|-------------------------|---------------------------------------------------|---------------------------------------------------|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Identification>|Não|Não|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>|Sim|Não|  
|<xref:System.Security.Principal.TokenImpersonationLevel.Delegation>|Sim|Sim|  
  
 O exemplo de código a seguir demonstra como usar a delegação.  
  
 [!code-csharp[c_delegation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_delegation/cs/source.cs#1)]
 [!code-vb[c_delegation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_delegation/vb/source.vb#1)]  
  
### <a name="how-to-configure-an-application-to-use-constrained-delegation"></a>Como configurar um aplicativo para usar a delegação restrita  
 Antes de você poder usar restrita delegação, o remetente, destinatário e o controlador de domínio deve ser configurado para fazer isso. O procedimento a seguir lista as etapas que permitem que a delegação restrita. Para obter detalhes sobre as diferenças entre a delegação e a delegação restrita, consulte a parte de [extensões Kerberos do Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=100194) que discute discussão restrita.  
  
1.  No controlador de domínio, desmarque o **conta é confidencial e não pode ser delegada** caixa de seleção para a conta sob a qual o aplicativo cliente está em execução.  
  
2.  No controlador de domínio, selecione o **a conta é confiável para delegação** caixa de seleção para a conta sob a qual o aplicativo cliente está em execução.  
  
3.  No controlador de domínio, configure o computador de camada intermediária para que seja confiável para delegação, clicando o **confiar no computador para delegação** opção.  
  
4.  No controlador de domínio, configure o computador de camada intermediária para usar a delegação restrita, clicando o **confiar no computador para delegação apenas a serviços especificados** opção.  
  
 Para obter instruções mais detalhadas sobre como configurar a delegação restrita, consulte os tópicos a seguir no MSDN:  
  
-   [Solucionando problemas de delegação de Kerberos](http://go.microsoft.com/fwlink/?LinkId=36724)  
  
-   [Transição de protocolo Kerberos e delegação restrita](http://go.microsoft.com/fwlink/?LinkId=36725)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>  
 <xref:System.ServiceModel.ImpersonationOption>  
 <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>  
 <xref:System.ServiceModel.ServiceSecurityContext>  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ImpersonateCallerForAllOperations%2A>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ChannelFactory%601>  
 <xref:System.Security.Principal.TokenImpersonationLevel.Identification>  
 [Usando a representação com segurança de transporte](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [Representar o cliente](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [Como representar um cliente em um serviço](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
