---
title: "Serviços de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
caps.latest.revision: "28"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 509da8b697f38ea75d9509a8243f3e9e09cc661b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="securing-services"></a>Serviços de segurança
Segurança de um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço consiste em dois requisitos principais: transferir a segurança e a autorização. (Um terceiro requisito, a auditoria de eventos de segurança, é descrita em [auditoria](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Em suma, a segurança de transferência inclui integridade (para detectar violação de assinatura digital), confidencialidade (criptografia de mensagens) e autenticação (verificar a identidade do serviço e o cliente). Autorização é o controle de acesso a recursos, por exemplo, permitindo que apenas usuários com privilégios ler um arquivo. Usando recursos do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], os dois principais requisitos facilmente são implementados.  
  
 Com exceção do <xref:System.ServiceModel.BasicHttpBinding> classe (ou o [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento na configuração), segurança de transferência é habilitada por padrão para todas as associações predefinidas. Os tópicos nesta seção abordam dois cenários básicos: Implementando a segurança de transferência e autorização em um serviço de intranet hospedado no Internet Information Services (IIS) e implementar a segurança de transferência e a autorização em um serviço hospedado no IIS.  
  
> [!NOTE]
>  Windows XP Home não dá suporte a autenticação do Windows. Portanto, você não deve executar um serviço no sistema.  
  
## <a name="security-basics"></a>Noções básicas sobre segurança  
 A segurança depende *credenciais*. Uma credencial prova que uma entidade é quem ele alega ser. (Um *entidade* pode ser uma pessoa, um processo de software, uma empresa ou qualquer coisa que pode ser autorizado.) Por exemplo, um cliente de um serviço faz um *declaração* de *identidade*, e a credencial comprova essa declaração em alguma forma. Um cenário típico, ocorre uma troca de credenciais. Primeiro, um serviço faz com que uma declaração de sua identidade e prova que ele para o cliente com uma credencial. Por outro lado, o cliente faz uma declaração de identidade e apresenta uma credencial para o serviço. Se ambas as partes confiar credenciais do outro, em seguida, um *contexto seguro* podem ser estabelecidos no qual todas as mensagens são trocadas na confidencialidade, e todas as mensagens são assinadas para proteger sua integridade. Depois que o serviço estabelece a identidade do cliente, em seguida, ela pode corresponder as declarações a credencial para um *função* ou *associação* em um grupo. Em ambos os casos, usando a função ou o grupo ao qual o cliente pertence, o serviço *autoriza* o cliente para executar um conjunto limitado de operações dependendo dos privilégios de função ou grupo.  
  
## <a name="windows-security-mechanisms"></a>Mecanismos de segurança do Windows  
 Se o cliente e o computador de serviço estiverem em um domínio do Windows que requer para fazer logon rede, as credenciais são fornecidas pela infraestrutura do Windows. Nesse caso, as credenciais são estabelecidas quando um usuário faz logon na rede. Cada usuário e cada computador na rede devem ser validadas como pertencente ao conjunto de usuários e computadores confiável. Em um sistema Windows, o usuário existe e o computador também é conhecido como um *entidade de segurança*.  
  
 Em um domínio do Windows com o apoio de um *Kerberos* controlador, o controlador de Kerberos usa um esquema baseado na concessão de permissões para cada entidade de segurança. Os tíquetes de concessões do controlador são confiáveis por outros tíquete granters no sistema. Sempre que uma entidade tenta executar alguma operação ou acesso uma *recurso* (como um arquivo ou diretório em um computador), o tíquete é examinado para sua validade e, se ele for aprovada, a entidade de segurança é concedida a outra permissão para a operação. Esse método de concessão de tíquetes é mais eficiente do que a alternativa de tentar validar a entidade de segurança para cada operação.  
  
 Um mecanismo mais antigo e menos segura usado nos domínios do Windows é NT LAN Manager (NTLM). Em casos onde o Kerberos não pode ser usado (normalmente fora de um domínio do Windows, como em um grupo de trabalho), o NTLM pode ser usado como uma alternativa. NTLM também está disponível como uma opção de segurança para o IIS.  
  
 Em um sistema Windows, autorização funciona por meio da atribuição de cada computador e usuário para um conjunto de funções e grupos. Por exemplo, cada computador do Windows deve configurar e controlado por uma pessoa (ou grupo de pessoas) na função do *administrador*. Outra função é que o *usuário*, que tem um conjunto muito mais restrito de permissões. Além da função, os usuários são atribuídos a grupos. Um grupo permite que vários usuários executar na mesma função. Na prática, portanto, uma máquina Windows é administrada por atribuir usuários a grupos. Por exemplo, vários usuários podem ser atribuídos ao grupo de usuários de um computador e um conjunto muito mais restrito de usuários pode ser atribuído ao grupo de administradores. Em um computador local, um administrador também pode criar novos grupos e atribuir outros usuários (ou outros grupos) para o grupo.  
  
 Em um computador executando o Windows, todas as pastas em um diretório podem ser protegidas. Ou seja, você pode selecionar uma pasta e controlar quem pode acessar os arquivos, e se ou não pode copiar o arquivo ou (no caso mais privilegiado) alterar um arquivo, excluir um arquivo ou adicionar arquivos à pasta. Isso é conhecido como controle de acesso e o mecanismo para que ele é conhecido como a lista de controle de acesso (ACL). Ao criar a ACL, você pode atribuir privilégios de acesso para qualquer grupo ou grupos, bem como os membros individuais de um domínio.  
  
 O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infraestrutura é projetada para usar esses mecanismos de segurança do Windows. Portanto, se você estiver criando um serviço que é implantado em uma intranet, e cujos clientes são restritos aos membros do domínio do Windows, segurança facilmente é implementada. Somente os usuários válidos podem fazer logon no domínio. Depois que os usuários fizerem logon, o controlador de Kerberos permite que cada usuário estabelecer contextos seguros com qualquer outro computador ou aplicativo. Em um computador local, grupos podem ser criados facilmente e, ao proteger pastas específicas, esses grupos podem ser usados para atribuir privilégios de acesso no computador.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementação de segurança do Windows em serviços da Intranet  
 Para proteger um aplicativo executado exclusivamente em um domínio do Windows, você pode usar as configurações de segurança padrão do <xref:System.ServiceModel.WSHttpBinding> ou <xref:System.ServiceModel.NetTcpBinding> associação. Por padrão, qualquer pessoa no mesmo domínio do Windows pode acessar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços. Como esses usuários fazer logon na rede, eles são confiáveis. As mensagens entre um serviço e um cliente são criptografadas para confidencialidade e assinadas para integridade. [!INCLUDE[crabout](../../../includes/crabout-md.md)]como criar um serviço que usa a segurança do Windows, consulte [como: proteger um serviço com as credenciais do Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autorização usando a PrincipalPermissionAttribute Class  
 Se você precisa restringir o acesso de recursos em um computador, a maneira mais fácil é usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe. Este atributo permite restringir a invocação de operações de serviço, exigindo que o usuário estar em um grupo do Windows especificado ou função, ou se um usuário específico. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Como: restringir o acesso com a PrincipalPermissionAttribute Class](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Representação  
 A representação é outro mecanismo que você pode usar para controlar o acesso aos recursos. Por padrão, um serviço hospedado pelo IIS será executado sob a identidade da conta ASPNET. A conta ASPNET pode acessar somente os recursos para os quais ele tem permissão. No entanto, é possível definir a ACL para uma pasta para excluir a conta de serviço do ASPNET, mas permite que determinadas outras identidades acessar a pasta. A pergunta, em seguida, torna-se como permitir que os usuários acessar a pasta se a conta ASPNET não tem permissão para fazer isso. A resposta é usar a representação, na qual o serviço pode usar as credenciais do cliente para acessar um recurso específico. Outro exemplo é ao acessar um banco de dados do SQL Server para que somente determinados usuários tem permissão. [!INCLUDE[crabout](../../../includes/crabout-md.md)]usando a representação, consulte [como: representar um cliente em um serviço](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) e [delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Segurança da Internet  
 Segurança na Internet consiste os mesmos requisitos de segurança em uma intranet. Um serviço precisa apresentar suas credenciais para comprovar a autenticidade e os clientes precisam provar sua identidade para o serviço. Depois que a identidade do cliente é aprovada, o serviço pode controlar quanto o cliente do acesso aos recursos. No entanto, devido à natureza heterogênea da Internet, as credenciais apresentadas diferem daqueles usados em um domínio do Windows. Enquanto um controlador de Kerberos lida com a autenticação de usuários em um domínio com permissões para as credenciais, na Internet, clientes e serviços confiam em qualquer uma das várias maneiras diferentes para apresentar as credenciais. No entanto, é o objetivo deste tópico apresentar uma abordagem comum que permite que você crie um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço está acessível na Internet.  
  
### <a name="using-iis-and-aspnet"></a>Usando o IIS e ASP.NET  
 Os requisitos de segurança da Internet e os mecanismos de resolver esses problemas, não são novos. O IIS é o servidor da Web da Microsoft para a Internet e tem muitos recursos de segurança que resolvem esses problemas. Além disso, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] inclui recursos de segurança que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviços podem usar. Para tirar proveito desses recursos de segurança, hospedar uma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço no IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Usando a associação do ASP.NET e provedores de função  
 O ASP.NET inclui um provedor de associação e funções. O provedor é um banco de dados de pares de nome/senha do usuário para autenticar chamadores que também permite que você especifique os privilégios de acesso do cada chamador. Com [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], você pode usar facilmente um provedor de função por meio da configuração e a associação já existente. Para um aplicativo de exemplo que demonstra isso, consulte o [provedor de função e associação](../../../docs/framework/wcf/samples/membership-and-role-provider.md) exemplo.  
  
### <a name="credentials-used-by-iis"></a>Credenciais usadas pelo IIS  
 Ao contrário de um domínio do Windows com o apoio de um controlador de Kerberos, a Internet é um ambiente sem um único controlador para gerenciar os milhões de usuários que fizerem logon qualquer momento. Em vez disso, as credenciais na Internet são geralmente na forma de certificados x. 509 (também conhecidos como certificados de Secure Sockets Layer ou SSL,). Normalmente, esses certificados são emitidos por uma *autoridade de certificação*, que pode ser uma empresa de terceiros que atesta a autenticidade do certificado e a pessoa tiver sido emitida para. Para expor o serviço na Internet, você também deve fornecer um certificado confiável para autenticar o serviço.  
  
 A pergunta surge neste ponto, como obter um certificado? É uma abordagem ir para uma autoridade de certificação de terceiros, como VeriSign, ou de Authenticode quando estiver pronto para implantar seu serviço e adquirir um certificado para o serviço. No entanto, se você estiver na fase de desenvolvimento com [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e ainda não está pronto para confirmar a compra um certificado, ferramentas e técnicas existem para a criação de certificados x. 509 que você pode usar para simular uma implantação de produção. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Trabalhar com certificados](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Modos de segurança  
 Programação [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] segurança envolve alguns pontos de decisão crítica. Um dos mais básica é a opção de *modo de segurança*. Os dois modos de segurança principal *o modo de transporte* e *modo de mensagem*.  
  
 É um modo de terceiro, que combina a semântica de ambos os modos principais, *transporte com modo de mensagem de credenciais*.  
  
 O modo de segurança determina como as mensagens são protegidas, e cada opção tem vantagens e desvantagens, conforme explicado a seguir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]definir o modo de segurança, consulte [como: definir o modo de segurança](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Modo de transporte  
 Há várias camadas entre a rede e o aplicativo. Um deles é o *transporte* camada*,* que gerencia a transferência de mensagens entre pontos de extremidade. Para a finalidade de presente, só é necessário entender que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usa vários protocolos de transporte, cada um deles pode proteger a transferência de mensagens. ([!INCLUDE[crabout](../../../includes/crabout-md.md)] transportes, consulte [transportes](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Um protocolo comumente usado é HTTP; outra vantagem é TCP. Cada um desses protocolos pode proteger específico de transferência por um mecanismo (ou mecanismos) da mensagem para o protocolo. Por exemplo, o protocolo HTTP é protegido usando SSL sobre HTTP, frequentemente abreviado como "HTTPS". Assim, quando você seleciona o modo de transporte para segurança, você escolhe usar o mecanismo, conforme determinado pelo protocolo. Por exemplo, se você selecionar o <xref:System.ServiceModel.WSHttpBinding> classe e defina o modo de segurança de transporte, você está selecionando SSL sobre HTTPS (HTTP) como o mecanismo de segurança. A vantagem do modo de transporte é que é mais eficiente do que o modo de mensagem porque a segurança é integrada em um nível relativamente baixo. Ao usar o modo de transporte, o mecanismo de segurança deve ser implementado de acordo com a especificação para o transporte e, portanto, as mensagens podem fluir com segurança apenas de ponto a ponto por meio do transporte.  
  
#### <a name="message-mode"></a>Modo de mensagem  
 Em contraste, o modo de mensagem fornece segurança, incluindo os dados de segurança como parte de cada mensagem. Usando XML e cabeçalhos de segurança SOAP, as credenciais e outros dados necessários para garantir que a integridade e confidencialidade da mensagem são incluídas com cada mensagem. Cada mensagem inclui dados de segurança, para que ele resulta em um pedágio em desempenho porque cada mensagem deve ser processada individualmente. (No modo de transporte, depois que a camada de transporte estiver protegida, todas as mensagens de fluxo livremente.) No entanto, a segurança de mensagem tem uma vantagem sobre a segurança de transporte: é mais flexível. Ou seja, os requisitos de segurança não são determinados pelo transporte. Você pode usar qualquer tipo de credencial de cliente para proteger a mensagem. (No modo de transporte, o protocolo de transporte determina o tipo de credencial de cliente que você pode usar).  
  
#### <a name="transport-with-message-credentials"></a>Transporte com credenciais de mensagem  
 O modo de terceiro combina o melhor de segurança de transporte e de mensagem. Nesse modo, a segurança de transporte é usada para garantir que a confidencialidade e a integridade de todas as mensagens com eficiência. Ao mesmo tempo, cada mensagem inclui seus dados de credencial, o que permite que a mensagem seja autenticado. Com a autenticação, autorização também pode ser implementada. Autenticando um remetente, acesso a recursos pode ser concedido (ou negado) de acordo com a identidade do remetente.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Especificando o tipo de credencial de cliente e o valor de credencial  
 Depois de selecionar um modo de segurança, você talvez queira especificar um tipo de credencial de cliente. O tipo de credencial de cliente especifica o tipo de um cliente deve usar para se autenticar no servidor.  
  
 Nem todos os cenários exigem um tipo de credencial de cliente, no entanto. Usando SSL sobre HTTPS (HTTP), um serviço se autentica o cliente. Como parte desta autenticação, o certificado do serviço é enviado ao cliente em um processo chamado *negociação*. O transporte protegido por SSL garante que todas as mensagens são confidenciais.  
  
 Se você estiver criando um serviço que exige que o cliente seja autenticado, sua escolha de um tipo de credencial de cliente depende de transporte e o modo selecionado. Por exemplo, usando o transporte HTTP e escolhendo o modo de transporte oferece várias opções, como Basic, Digest e outros. ([!INCLUDE[crabout](../../../includes/crabout-md.md)] esses tipos de credenciais, consulte [Noções básicas sobre a autenticação HTTP](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 Se você estiver criando um serviço em um domínio do Windows que estará disponível somente para outros usuários da rede, o mais fácil de usar é o tipo de credencial de cliente do Windows. No entanto, você também precisará fornecer um serviço com um certificado. Isso é mostrado no [como: especificar valores de credencial de cliente](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Valores de credencial  
 Um *valor de credencial* é real usa o serviço de credencial. Depois que você especificou um tipo de credencial, você talvez precise configurar o serviço com as credenciais reais. Se você selecionou Windows (e o serviço será executado em um domínio do Windows), você não especificar um valor de credencial real.  
  
## <a name="identity"></a>Identidade  
 Em [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], o termo *identidade* tem significados diferentes para o servidor e o cliente. Em suma, quando um serviço em execução, uma identidade é atribuída para o contexto de segurança após a autenticação. Para exibir a identidade real, verifique o <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> propriedades da <xref:System.ServiceModel.ServiceSecurityContext> classe. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Como: Examine o contexto de segurança](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Por outro lado, no cliente, a identidade é usada para validar o serviço. Em tempo de design, um desenvolvedor de cliente pode definir o [ \<identidade >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento para um valor obtido do serviço. Em tempo de execução, o cliente verifica o valor do elemento em relação a identidade real do serviço. Se a verificação falhar, o cliente encerra a comunicação. O valor pode ser um nome de usuário principal (UPN) se o serviço é executado sob a identidade de um usuário específico ou um nome de entidade de serviço (SPN) se o serviço é executado sob uma conta de computador. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Autenticação e identidade de serviço](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). A credencial também pode ser um certificado ou um campo encontrado em um certificado que identifica o certificado.  
  
## <a name="protection-levels"></a>Níveis de proteção  
 O `ProtectionLevel` propriedade ocorre em várias classes de atributo (como o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> classes). O nível de proteção é um valor que especifica se as mensagens (ou partes da mensagem) que dão suporte a um serviço são assinados, assinado e criptografado ou enviados sem criptografia ou assinaturas. [!INCLUDE[crabout](../../../includes/crabout-md.md)]a propriedade, consulte [Noções básicas sobre nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md)e para obter exemplos de programação, consulte [como: definir a propriedade ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Projetando um contrato de serviço com o `ProtectionLevel` no contexto, consulte [criar contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Autenticação e identidade de serviço](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md) (Noções básicas de nível de proteção)  
 [Delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) (Criando contratos de serviço)  
 [Segurança](../../../docs/framework/wcf/feature-details/security.md)  
 [Visão geral de segurança](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [How to: Set the ProtectionLevel Property](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) (Como definir a propriedade ProtectionLevel)  
 [How to: Secure a Service with Windows Credentials](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md) (Como proteger um serviço com credenciais Windows)  
 [How to: Set the Security Mode](../../../docs/framework/wcf/how-to-set-the-security-mode.md) (Como definir o modo de segurança)  
 [How to: Specify the Client Credential Type](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md) (Como especificar o tipo de credencial do cliente)  
 [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md) (Como restringir o acesso com a classe PrincipalPermissionAttribute)  
 [How to: Impersonate a Client on a Service](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) (Como representar um cliente em um serviço)  
 [How to: Examine the Security Context](../../../docs/framework/wcf/how-to-examine-the-security-context.md) (Como examinar o contexto de segurança)
