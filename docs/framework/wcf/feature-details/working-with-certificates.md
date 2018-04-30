---
title: Trabalhando com certificados
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
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c023b27ace10919c51aa13e2635040d9d5b812b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="working-with-certificates"></a>Trabalhando com certificados
Para programar a segurança do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], os certificados digitais X.509 são normalmente usados para autenticar clientes e servidores, criptografar e assinar mensagens digitalmente. Este tópico explica rapidamente os recursos do certificado digital X.509 e como usá-los no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], e inclui links para tópicos que explicam esses conceitos ainda mais ou que mostram como realizar tarefas comuns usando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e certificados.  
  
 Em suma, um certificado digital faz parte de um *infraestrutura de chave pública* (PKI), que é um sistema de certificados digitais, autoridades de certificação e outras autoridades de registro que verificam e autenticam a validade de cada parte envolvida em uma transação eletrônica com o uso de criptografia de chave pública. Uma autoridade de certificação emite certificados e cada certificado tem um conjunto de campos que contêm dados, como *assunto* (a entidade à qual o certificado é emitido), as datas de validade (quando o certificado é válido), (o emissor entidade que emitiu o certificado) e uma chave pública. No [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], cada uma dessas propriedades é processada como um <xref:System.IdentityModel.Claims.Claim> e cada afirmação é dividida ainda mais em dois tipos: identidade e direito. Para obter mais informações sobre o x. 509 certificados Consulte [certificados de chave pública x. 509](http://go.microsoft.com/fwlink/?LinkId=209952)para obter mais informações sobre declarações e autorização no consulte WCF [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md). Para obter mais informações sobre como implementar uma PKI, consulte [Windows Server 2008 R2 - serviços de certificados](http://go.microsoft.com/fwlink/?LinkId=209949).  
  
 Uma função principal do certificado é autenticar a identidade do proprietário do certificado para outros. Um certificado contém a *chave pública* do proprietário, enquanto o proprietário retém a chave privada. A chave pública pode ser usada para criptografar as mensagens enviadas para o proprietário do certificado. Somente o proprietário tem acesso à chave privada; portanto, somente o proprietário pode descriptografar essas mensagens.  
  
 Os certificados devem ser emitidos por uma autoridade de certificação, que é normalmente um distribuidor de certificados de terceiros. Em um domínio do Windows, uma autoridade de certificação é incluída e pode ser usada para emitir certificados para computadores no domínio.  
  
## <a name="viewing-certificates"></a>Exibindo certificados  
 Para trabalhar com certificados, geralmente é necessário exibi-los e examinar suas propriedades. Isso é feito facilmente com a ferramenta de snap-in do Console de Gerenciamento Microsoft (MMC). Para obter mais informações, consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Repositórios de certificados  
 Os certificados estão localizados em repositórios. Dois grandes repositórios de certificado existem e são divididos em sub-repositórios. Se você for o administrador em um computador, poderá exibir os dois principais repositórios usando a ferramenta do snap-in do MMC. Os não administradores podem exibir somente o repositório do usuário atual.  
  
-   **O repositório de computador local**. Ele contém os certificados acessados por processos do computador, como [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Use este local para armazenar os certificados que autenticam o servidor para clientes.  
  
-   **O armazenamento do usuário atual**. Os aplicativos interativos geralmente colocam certificados aqui para o usuário atual do computador. Se você estiver criando um aplicativo cliente, aqui é onde você normalmente coloca os certificados que autenticam um usuário para um serviço.  
  
 Esses dois repositórios são divididos em sub-repositórios. O mais importante deles ao programar com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclui:  
  
-   **Autoridades de certificação raiz confiáveis**. Você pode usar os certificados nesse repositório para criar uma cadeia de certificados, que podem ser rastreados para um certificado de autoridade de certificação nesse repositório.  
  
    > [!IMPORTANT]
    >  O computador local implicitamente confia em qualquer certificado colocado nesse repositório, mesmo se o certificado não vier de uma autoridade de certificação de terceiros confiável. Por esse motivo, não coloque nenhum certificado nesse repositório a menos que você confie totalmente no emissor e entenda as consequências.  
  
-   **Pessoais**. Esse repositório é usado para os certificados associados com um usuário de um computador. Geralmente, esse repositório é usado para os certificados emitidos por um dos certificados da autoridade de certificação localizados no repositório Autoridades de Certificação Confiáveis. Como alternativa, um certificado localizado aqui pode ser emitido por conta própria e confiável por um aplicativo.  
  
 Para obter mais informações sobre repositórios de certificados, consulte [repositórios de certificados](http://go.microsoft.com/fwlink/?LinkId=88912).  
  
### <a name="selecting-a-store"></a>Selecionando um repositório  
 Selecionar onde armazenar um certificado depende de como e quando o serviço ou o cliente é executado. As seguintes regras gerais se aplicam:  
  
-   Se o serviço do WCF é hospedado em um uso de serviço do Windows a **máquina local** armazenar. Observe que os privilégios de administrador são necessários para instalar certificados no repositório do computador local.  
  
-   Se o serviço ou cliente é um aplicativo que é executado sob uma conta de usuário, use o **usuário atual** armazenar.  
  
### <a name="accessing-stores"></a>Acessando repositórios  
 Os repositórios são protegidos por listas de controle de acesso (ACLs), como pastas em um computador. Ao criar um serviço hospedado pelos Serviços de Informações da Internet (IIS), o processo do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] é executado sob a conta do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Essa conta deve ter acesso ao repositório que contém os certificados que um serviço usa. Cada um dos principais repositórios é protegido por uma lista de acesso padrão, mas as listas podem ser modificadas. Se você criar uma função separada para acessar um repositório, deverá conceder permissão de acesso a essa função. Para saber como modificar a lista de acesso usando a ferramenta WinHttpCertConfig.exe, consulte [como: criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md). Para obter mais informações sobre como usar certificados de cliente com o IIS, consulte [como chamar um serviço Web usando um certificado de cliente para autenticação em um aplicativo Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=88914).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Confiança de cadeia e autoridades de certificado  
 Os certificados são criados em uma hierarquia onde cada certificado individual está vinculado à CA que emitiu o certificado. Este é o link para o certificado da CA. O certificado da CA em seguida vincula à CA que emitiu o certificado da CA original. Esse processo é repetido até que o certificado da CA seja alcançado. O certificado da CA é inerentemente de confiança.  
  
 Certificados digitais são usados para autenticar uma entidade confiando essa hierarquia, também chamada de um *cadeia de confiança*. Você pode exibir a cadeia de qualquer certificado usando o snap-in do MMC clicando duas vezes em qualquer certificado, em seguida, clicando no **caminho do certificado** guia. Para obter mais informações sobre como importar cadeias de certificados para uma autoridade de certificação, consulte [como: especificar o certificado de autoridade de certificado cadeia usada para verificar assinaturas](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Qualquer emissor pode ser designado uma autoridade confiável colocando o certificado do emissor no repositório de certificados da autoridade confiável.  
  
### <a name="disabling-chain-trust"></a>Desabilitando a cadeia de confiança  
 Ao criar um novo serviço, você pode usar um certificado que não seja emitido por um certificado raiz confiável ou o próprio certificado de emissão pode não estar no repositório das Autoridades de Certificação Confiáveis. Somente para a finalidade de desenvolvimento, você pode desativar temporariamente o mecanismo que verifica a cadeia de confiança para um certificado. Para fazer isso, defina a propriedade `CertificateValidationMode` para `PeerTrust` ou `PeerOrChainTrust`. Qualquer um dos modos especifica que o certificado pode ser emitido por conta própria (confiança de par) ou parte de uma cadeia de confiança. Você pode definir a propriedade em qualquer uma das seguintes classes.  
  
|Classe|Propriedade|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Também é possível definir a propriedade usando configuração. Os seguintes elementos são usados para especificar o modo de validação:  
  
-   [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Autenticação personalizada  
 A propriedade `CertificateValidationMode` também permite que você personalize como os certificados são autenticados. Por padrão, o nível é definido como `ChainTrust`. Para usar o valor <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, você também deverá definir o atributo `CustomCertificateValidatorType` para um assembly e um tipo usados para validar o certificado. Para criar um validador personalizado, você deverá herdar da classe abstrata <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
 Ao criar um autenticador personalizado, o método mais importante para substituição é o método <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>. Para obter um exemplo de autenticação personalizada, consulte o [validador de certificado x. 509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) exemplo. Para obter mais informações, consulte [credencial personalizada e validação de credencial](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-makecertexe-to-build-a-certificate-chain"></a>Usando Makecert.exe para criar uma cadeia de certificado  
 A ferramenta de criação de certificado (Makecert.exe) cria certificados X.509 e pares de chave privada/chave pública. Você pode salvar a chave privada no disco e, em seguida, usá-la para emitir e assinar novos certificados, simulando uma hierarquia de certificados encadeados. A ferramenta é destinada para uso somente como uma ajuda ao desenvolver serviços e nunca deve ser usada para criar certificados para implantação real. Ao desenvolver um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], use as seguintes etapas para criar uma cadeia de confiança com Makecert.exe.  
  
#### <a name="to-build-a-chain-of-trust-with-makecertexe"></a>Para criar uma cadeia de confiança com Makecert.exe  
  
1.  Crie um certificado temporário de autoridade (autoassinado) usando a ferramenta MakeCert.exe. Salve a chave privada no disco.  
  
2.  Use o novo certificado para emitir outro certificado que contém a chave pública.  
  
3.  Importe o certificado de autoridade no repositório de Autoridades de Certificação Confiáveis.  
  
4.  Para obter instruções passo a passo, consulte [como: criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Qual certificado usar?  
 As perguntas comuns sobre certificados são qual certificado usar e por quê. A resposta depende de se você está programando um cliente ou serviço. As informações a seguir fornecem uma orientação geral e não são uma resposta completa a essas perguntas.  
  
### <a name="service-certificates"></a>Certificados de serviço  
 Os certificados de serviço têm a tarefa principal de autenticar o servidor para clientes. Uma das verificações inicias quando um cliente autenticado a um servidor é comparar o valor da **assunto** campo para o URI Uniform Resource Identifier () usado para contatar o serviço: o DNS de ambos devem corresponder. Por exemplo, se o URI do serviço é "http://www.contoso.com/endpoint/" o **assunto** campo também deve conter o valor "www.contoso.com".  
  
 Observe que o campo pode conter vários valores, cada um prefixado com uma inicialização para indicar o valor. Mais comumente, a inicialização é “CN” para o nome comum, por exemplo, "CN = www.contoso.com". Também é possível que o **assunto** campo em branco, caso em que o **nome alternativo da entidade** campo pode conter o **nome DNS** valor.  
  
 Também observe o valor da **finalidades** campo do certificado deve incluir um valor apropriado, como "Autenticação do servidor" ou "Autenticação do cliente".  
  
### <a name="client-certificates"></a>Certificados de cliente  
 Os certificados de cliente não são normalmente emitidos por uma autoridade de certificação de terceiros. Em vez disso, o repositório Pessoal do local atual do usuário geralmente contém os certificados colocados lá por uma autoridade raiz, com uma finalidade de “Autenticação do cliente”. O cliente pode usar um certificado quando a autenticação mútua é necessária.  
  
## <a name="online-revocation-and-offline-revocation"></a>Revogação online e revogação offline  
  
### <a name="certificate-validity"></a>Validade de certificado  
 Cada certificado é válido somente para um determinado período de tempo, chamado de *validade*. O período de validade é definido pelo **válida de** e **válida para** campos de um certificado x. 509. Durante a autenticação, o certificado é verificado para determinar se o certificado ainda está dentro do período de validade.  
  
### <a name="certificate-revocation-list"></a>Lista de revogação de certificados  
 A qualquer momento durante o período de validade, a autoridade de certificação pode revogar um certificado. Isso pode ocorrer por muitas razões, como um comprometimento da chave privada do certificado.  
  
 Quando isso ocorre, todas as cadeias que descenderem do certificado revogado também tornam-se inválidas e não são confiáveis durante os procedimentos de autenticação. Para descobrir quais certificados são revogados, cada emissor publica uma hora e data-marcada *lista de certificados revogados* (CRL). A lista pode ser marcada usando a revogação online ou offline definindo a propriedade `RevocationMode` ou `DefaultRevocationMode` das seguintes classes para um dos valores de enumeração <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>: as classes <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> e <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>. O valor padrão para todas as propriedades é `Online`.  
  
 Você também pode definir o modo de configuração usando o `revocationMode` atributo de ambos os [ \<autenticação >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (da [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) e o [ \<autenticação >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (da [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>O método SetCertificate  
 No [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você deve geralmente especificar um certificado ou conjunto de certificados que um serviço ou cliente deve usar para autenticar, criptografar ou assinar digitalmente uma mensagem. Você pode fazer isso por meio de programação usando o método `SetCertificate` de várias classes que representam certificados X.509. As seguintes classes usam o método `SetCertificate` para especificar um certificado.  
  
|Classe|Método|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 O método `SetCertificate` funciona designando um local de repositório e um repositório, um tipo “find” (parâmetro `x509FindType`) que especifica um campo do certificado e um valor a ser localizado no campo. Por exemplo, o código a seguir cria um <xref:System.ServiceModel.ServiceHost> instância e define o certificado de serviço usado para autenticar o serviço para clientes com o `SetCertificate` método.  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Vários certificados com o mesmo valor  
 Um repositório pode conter vários certificados com o mesmo nome de assunto. Isso significa que, se você especificar que o `x509FindType` é <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> ou <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>e mais de um certificado tem o mesmo valor, uma exceção será lançada porque não há nenhuma forma de distinguir qual certificado é necessário. Você pode solucionar isso configurando o `x509FindType` como <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. O campo de impressão digital contém um valor exclusivo que pode ser usado para localizar um certificado específico em um repositório. No entanto, isso tem sua própria desvantagem: se o certificado for revogado ou renovado, o método `SetCertificate` falhará porque a impressão digital também será. Ou se o certificado não for mais válido, a autenticação falhará. A maneira de solucionar isso é definir o parâmetro `x590FindType` como <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> e especificar o nome do emissor. Se nenhum emissor específico for necessário, você também poderá definir um dos outros valores de enumeração <xref:System.Security.Cryptography.X509Certificates.X509FindType>, como <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Certificados na configuração  
 Você também pode definir certificados usando configuração. Se você estiver criando um serviço, as credenciais, incluindo certificados, são especificadas sob o [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Quando você estiver programando um cliente, os certificados são especificados sob o [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Mapeando um certificado para uma conta de usuário  
 Um recurso do IIS e do Active Directory é a capacidade para mapear um certificado para uma conta de usuário do Windows. Para obter mais informações sobre o recurso, consulte [mapear certificados para contas de usuário](http://go.microsoft.com/fwlink/?LinkId=88917).  
  
 Para obter mais informações sobre como usar o mapeamento do Active Directory, consulte [mapeamento de certificados de cliente com o mapeamento de serviço de diretório](http://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Com esse recurso ativado, você poderá definir a propriedade <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> da classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> como `true`. Na configuração, você pode definir o `mapClientCertificateToWindowsAccount` atributo do [ \<autenticação >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) elemento `true`, conforme mostrado no código a seguir.  
  
```xml  
<serviceBehaviors>  
 <behavior name="MappingBehavior">  
  <serviceCredentials>  
   <clientCertificate>  
    <authentication certificateValidationMode="None" mapClientCertificateToWindowsAccount="true" />  
   </clientCertificate>  
  </serviceCredentials>  
 </behavior>  
</serviceBehaviors>  
```  
  
 Mapear um certificado X.509 para o símbolo que representa uma conta de usuário do Windows é considerado uma elevação de privilégio. Assim que for mapeado, o símbolo do Windows poderá ser usado para conceder acesso aos recursos protegidos. Portanto, a política de domínio exige que o certificado X.509 esteja em conformidade com sua política antes do mapeamento. O *SChannel* pacote de segurança impõe esse requisito.  
  
 Ao usar [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] ou posterior, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] garante que o certificado esteja em conformidade com a política de domínio antes de ser mapeado para uma conta do Windows.  
  
 Na primeira versão do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], o mapeamento é feito sem consultar a política de domínio. Portanto, é possível que aplicativos mais antigos que funcionavam ao serem executados na primeira versão falhem se o mapeamento for habilitado e o certificado X.509 não atender a política de domínio.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels>  
 <xref:System.ServiceModel.Security>  
 <xref:System.ServiceModel>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
