---
title: Selecionando um tipo de credencial
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 27e1bc4b9e4209fafd0e3707ad6674eb5db6e451
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577107"
---
# <a name="selecting-a-credential-type"></a>Selecionando um tipo de credencial
*Credenciais* são os dados que usa o Windows Communication Foundation (WCF) para estabelecer uma identidade reivindicada ou recursos. Por exemplo, o passport é uma credencial que um governo emite para provar cidadania em um país ou região. No WCF, as credenciais podem assumir várias formas, como tokens de nome de usuário e certificados x. 509. Este tópico discute como selecionar o credencial correto para seu aplicativo, como eles são usados no WCF e credenciais.  
  
 Em muitos países e regiões, de motorista uma carteira é um exemplo de uma credencial. Uma licença contém dados que representa os recursos e a identidade de uma pessoa. Ele contém uma prova de posse na forma de imagem do detentor. A licença é emitida por uma autoridade confiável, normalmente, um departamento governamental de licenciamento. A licença é lacrada e pode conter um holograma, mostrando que ele não foi adulterado ou falsificado.  
  
 Apresentar uma credencial envolve a apresentar os dados e a prova de posse dos dados. O WCF oferece suporte a uma variedade de tipos de credenciais nos níveis de segurança de transporte e de mensagem. Por exemplo, considere dois tipos de credenciais com suporte no WCF: credenciais de certificado de nome de usuário e (x. 509).  
  
 Para a credencial de nome de usuário, o nome de usuário representa a identidade reivindicada e a senha fornece a prova de posse. Nesse caso, a autoridade confiável é o sistema que valida o nome de usuário e senha.  
  
 Com uma credencial de certificado x. 509, o nome da entidade, o nome alternativo da entidade ou a campos específicos no certificado podem ser usados como declarações de identidade, enquanto outros campos, tais como o `Valid From` e `Valid To` campos, especifique a validade das certificado.  
  
## <a name="transport-credential-types"></a>Tipos de credenciais de transporte  
 A tabela a seguir mostra os possíveis tipos de credenciais do cliente que podem ser usados por uma associação no modo de segurança de transporte. Ao criar um serviço, defina o `ClientCredentialType` propriedade a ser um destes valores para especificar o tipo de credencial que o cliente deve fornecer para se comunicar com seu serviço. Você pode definir os tipos nos arquivos de configuração ou código.  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nenhum|Especifica que o cliente não precisa apresentar nenhuma credencial. Isso se traduz em um cliente anônimo.|  
|Basic|Especifica a autenticação básica para o cliente. Para obter mais informações, consulte o RFC2617 –[autenticação HTTP: Autenticação Básica e Digest](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|Digest|Especifica a autenticação digest para o cliente. Para obter mais informações, consulte o RFC2617 –[autenticação HTTP: Autenticação Básica e Digest](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|NTLM|Especifica a autenticação NT LAN Manager (NTLM). Isso é usado quando você não pode usar a autenticação Kerberos por algum motivo. Você também pode desabilitar seu uso como um fallback definindo a <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> propriedade para `false`, que faz com que o WCF fazer um esforço para lançar uma exceção se NTLM for usado. Observe que a definição dessa propriedade `false` talvez não impeçam que as credenciais do NTLM sejam enviados durante a transmissão.|  
|Windows|Especifica autenticação do Windows. Para especificar apenas o protocolo Kerberos em um domínio do Windows, defina as <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> propriedade para `false` (o padrão é `true`).|  
|Certificado|Executa a autenticação de cliente usando um certificado X.509.|  
|Senha|Usuário deve fornecer um nome de usuário e senha. Valide o par de nome/senha de usuário usando a autenticação do Windows ou outra solução personalizada.|  
  
### <a name="message-client-credential-types"></a>Tipos de credencial de cliente de mensagem  
 A tabela a seguir mostra os tipos de credencial possíveis que você pode usar ao criar um aplicativo que usa a segurança de mensagem. Você pode usar esses valores em arquivos de configuração ou código.  
  
|Configuração|Descrição|  
|-------------|-----------------|  
|Nenhum|Especifica que o cliente não precisa apresentar uma credencial. Isso se traduz em um cliente anônimo.|  
|Windows|Permite que as trocas de mensagens SOAP ocorrer sob o contexto de segurança estabelecido com uma credencial do Windows.|  
|Nome de usuário|Permite que o serviço exigir que o cliente seja autenticado com uma credencial de nome de usuário. Observe que o WCF não permite todas as operações criptográficas com nomes de usuário, como gerar uma assinatura ou criptografia de dados. WCF garante que o transporte é protegido ao usar as credenciais de nome de usuário.|  
|Certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado X.509.|  
|Emitido de Token|Um tipo de token personalizado configurado de acordo com uma política de segurança. O tipo de token padrão é asserções marcação linguagem SAML (Security). O token é emitido por um serviço de token seguro. Para obter mais informações, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Modelo de negociação de credenciais de serviço  
 *Negociação* é o processo de estabelecer a relação de confiança entre um cliente e um serviço por meio da troca as credenciais. O processo é executado de forma iterativa entre o cliente e o serviço de modo a divulgar apenas as informações necessárias para a próxima etapa no processo de negociação. Na prática, o resultado final é o fornecimento de credenciais do serviço para o cliente a ser usado em operações subsequentes.  
  
 Com uma exceção, por padrão as associações fornecidas pelo sistema no WCF negociam a credencial de serviço automaticamente ao usar a segurança de nível de mensagem. (A exceção é o <xref:System.ServiceModel.BasicHttpBinding>, que não permite segurança por padrão.) Para desabilitar esse comportamento, consulte o <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> e <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> propriedades.  
  
> [!NOTE]
>  Quando segurança SSL é usada com o .NET Framework 3.5 e posterior, um cliente WCF usa tanto os certificados intermediários em seu repositório de certificados e os certificados intermediários recebidos durante a negociação SSL para executar a validação da cadeia de certificado do serviço certificado. .NET framework 3.0 usa apenas os certificados intermediários instalados no repositório de certificados local.  
  
#### <a name="out-of-band-negotiation"></a>Negociação de out-of-Band  
 Se a negociação automática estiver desabilitada, a credencial de serviço deve ser provisionada no cliente antes de enviar todas as mensagens para o serviço. Isso também é conhecido como um *out-of-band* provisionamento. Por exemplo, se o tipo de credencial especificado é um certificado e negociação automática está desabilitada, o cliente deverá contatar o proprietário do serviço para receber e instalar o certificado no computador que executa o aplicativo cliente. Isso pode ser feito, por exemplo, quando você deseja controlar rigidamente quais clientes podem acessar um serviço em um cenário de business-to-business. Essa fora-de-band-negociação pode ser feito no email e o certificado X.509 é armazenado no repositório de certificados do Windows, usando uma ferramenta como o snap-in de certificados do Microsoft Management Console (MMC).  
  
> [!NOTE]
>  O <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade é usada para fornecer o serviço com um certificado que foi obtido por meio de negociação de out-of-band. Isso é necessário ao usar o <xref:System.ServiceModel.BasicHttpBinding> classe porque a associação não permite negociação automatizada. A propriedade também é usada em um cenário de duplex não correlacionado. Isso é um cenário em que um servidor envia uma mensagem para o cliente sem a necessidade do cliente enviar uma solicitação ao servidor pela primeira vez. Porque o servidor não tem uma solicitação do cliente, ele deve usar o certificado do cliente para criptografar a mensagem ao cliente.  
  
## <a name="setting-credential-values"></a>Definindo valores de credencial  
 Depois de selecionar um modo de segurança, você deve especificar as credenciais reais. Por exemplo, se o tipo de credencial é definido como "certificado", você deve associar uma credencial específica (por exemplo, um certificado x. 509 específico) com o serviço ou cliente.  
  
 Dependendo se você estiver programando um cliente ou um serviço, o método para definir o valor de credencial é ligeiramente diferente.  
  
### <a name="setting-service-credentials"></a>Credenciais do serviço de configuração  
 Se você estiver usando o modo de transporte e você estiver usando HTTP como o transporte, você deve usar qualquer um dos serviços de informações da Internet (IIS) ou configurar a porta com um certificado. Para obter mais informações, consulte [visão geral da segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) e [segurança de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Para provisionar um serviço com credenciais no código, crie uma instância do <xref:System.ServiceModel.ServiceHost> de classe e especificar as credenciais apropriadas usando o <xref:System.ServiceModel.Description.ServiceCredentials> classe, acessado por meio de <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> propriedade.  
  
#### <a name="setting-a-certificate"></a>Configurar um certificado  
 Para provisionar um serviço com um certificado X.509 a ser usado para autenticar o serviço aos clientes, use o <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> classe.  
  
 Para provisionar um serviço com um certificado de cliente, use o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> classe.  
  
#### <a name="setting-windows-credentials"></a>Configurar as credenciais do Windows  
 Se o cliente especificar um nome de usuário válido e uma senha, essa credencial é usada para autenticar o cliente. Caso contrário, as credenciais de logon do usuário atual são usadas.  
  
### <a name="setting-client-credentials"></a>Configurar as credenciais do cliente  
 No WCF, os aplicativos cliente usar um cliente WCF para se conectar aos serviços. Deriva de todos os clientes a <xref:System.ServiceModel.ClientBase%601> classe e o <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade no cliente permite a especificação de vários valores de credenciais de cliente.  
  
#### <a name="setting-a-certificate"></a>Configurar um certificado  
 Para provisionar um serviço com um certificado X.509 que é usado para autenticar o cliente para um serviço, use o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método da <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> classe.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Como as credenciais do cliente são usadas para autenticar um cliente para o serviço  
 Informações de credenciais de cliente necessárias para se comunicar com um serviço são fornecidas usando o <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade ou o <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade. O canal de segurança usa essas informações para autenticar o cliente para o serviço. A autenticação é realizada por meio de um dos dois modos:  
  
-   As credenciais do cliente são usadas de uma vez antes da primeira mensagem é enviada usando a instância do cliente WCF para estabelecer um contexto de segurança. Todas as mensagens de aplicativo, em seguida, são protegidas por meio do contexto de segurança.  
  
-   As credenciais do cliente são usadas para autenticar cada mensagem de aplicativo enviada para o serviço. Nesse caso, nenhum contexto é estabelecido entre o cliente e o serviço.  
  
### <a name="established-identities-cannot-be-changed"></a>Identidades estabelecidas não podem ser alteradas.  
 Quando o primeiro método é usado, o contexto estabelecido é permanentemente associado com a identidade do cliente. Ou seja, quando o contexto de segurança tiver sido estabelecido, a identidade associada com o cliente não pode ser alterada.  
  
> [!IMPORTANT]
>  Há uma situação de estar ciente de quando a identidade não pode ser alternada (ou seja, quando estabelecer a segurança contexto estiver ativado, o comportamento padrão). Se você criar um serviço que se comunica com um segundo serviço, a identidade usada para abrir o cliente do WCF para o segundo serviço não pode ser alterada. Isso se torna um problema se vários clientes têm permissão para usar o primeiro serviço e o serviço representa os clientes ao acessar o serviço de segundo. Se o serviço reutiliza o mesmo cliente para todos os chamadores, todas as chamadas para o segundo serviço são realizadas sob a identidade do chamador primeiro que foi usado para abrir o cliente para o serviço de segundo. Em outras palavras, o serviço usa a identidade do cliente de primeira para todos os seus clientes para se comunicar com o segundo serviço. Isso pode levar à elevação de privilégio. Se isso não é o comportamento desejado do seu serviço, acompanhar cada chamador e criar um novo cliente para o serviço de segundo para todos os chamadores distintos e certifique-se de que o serviço usa somente o cliente correto para o chamador certo para se comunicar com o segundo serviço.  
  
 Para obter mais informações sobre credenciais e sessões seguras, consulte [considerações sobre segurança para sessões seguras](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [Conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Programação de segurança do WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Segurança de transporte de HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
