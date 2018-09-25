---
title: Serviços de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF], securing services
- WCF security
- WCF, security
ms.assetid: f0ecc6f7-f4b5-42a4-9cb1-b02e28e26620
author: BrucePerlerMS
ms.openlocfilehash: a97f1b96d6cf4d166239ba8e0a14f6e3af2bf48b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071053"
---
# <a name="securing-services"></a>Serviços de segurança
Segurança de um serviço do Windows Communication Foundation (WCF) consiste em dois requisitos principais: segurança e autorização de transferência. (Um terceiro requisito, a auditoria de eventos de segurança, é descrito em [auditoria](../../../docs/framework/wcf/feature-details/auditing-security-events.md).) Em suma, a segurança de transferência inclui autenticação (verificar a identidade do serviço e o cliente), confidencialidade (criptografia de mensagens) e integridade (para detectar violação de assinatura digital). A autorização é o controle de acesso a recursos, por exemplo, permitindo que apenas usuários com privilégios ler um arquivo. Usando recursos do WCF, os dois requisitos principais são implementados com facilidade.  
  
 Com exceção do <xref:System.ServiceModel.BasicHttpBinding> classe (ou o [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento na configuração), segurança de transferência está habilitada por padrão para todas as associações predefinidas. Os tópicos nesta seção abordam os dois cenários básicos: Implementando a segurança de transferência e autorização em um serviço de intranet hospedado no Internet Information Services (IIS) e implementar a segurança de transferência e a autorização em um serviço hospedado no IIS.  
  
> [!NOTE]
>  Windows XP Home não dá suporte a autenticação do Windows. Portanto, você não deve executar um serviço no sistema.  
  
## <a name="security-basics"></a>Noções básicas sobre segurança  
 A segurança depende *credenciais*. Uma credencial de prova que uma entidade é quem diz ser. (Um *entidade* pode ser uma pessoa, um processo de software, uma empresa ou qualquer coisa que pode ser autorizado.) Por exemplo, um cliente de um serviço faz uma *declaração* dos *identidade*, e a credencial prova dessa declaração de alguma maneira. Um cenário típico, ocorre uma troca de credenciais. Primeiro, um serviço faz uma declaração de sua identidade e comprove sua identidade para o cliente com uma credencial. Por outro lado, o cliente faz uma declaração de identidade e apresenta uma credencial para o serviço. Se ambas as partes do outro as credenciais de confiança, em seguida, um *contexto seguro* podem ser estabelecidos no quais todas as mensagens são trocadas de confidencialidade, e todas as mensagens são assinadas para proteger sua integridade. Depois que o serviço estabelece a identidade do cliente, ele pode corresponder, em seguida, as declarações na credencial para um *função* ou *associação* em um grupo. Em ambos os casos, usando a função ou o grupo ao qual o cliente pertence, o serviço *autoriza* o cliente a executar um conjunto limitado de operações com base nos privilégios de função ou grupo.  
  
## <a name="windows-security-mechanisms"></a>Mecanismos de segurança do Windows  
 Se o cliente e o computador de serviço estão em um domínio do Windows que requer dois para fazer logon rede, as credenciais são fornecidas pela infraestrutura do Windows. Nesse caso, as credenciais são estabelecidas quando um usuário fizer logon rede. Todos os usuários e todos os computadores na rede devem ser validadas como pertencentes ao conjunto confiável de usuários e computadores. Em um sistema Windows, o usuário existe e o computador também é conhecido como um *entidade de segurança*.  
  
 Em um domínio do Windows apoiado por um *Kerberos* controlador, o controlador de Kerberos usa um esquema com base na concessão de tíquetes para cada entidade de segurança. Os tíquetes as concessões de controlador são confiáveis por outros granters tíquete no sistema. Sempre que uma entidade tenta realizar alguma operação ou acesso uma *recurso* (por exemplo, um arquivo ou diretório em um computador), o tíquete é examinado quanto a sua validade e, se ele for aprovado, a entidade de segurança é concedida a outro tíquete para a operação. Esse método de concessão de tíquetes é mais eficiente do que a alternativa de tentar validar a entidade de segurança para cada operação.  
  
 Um mecanismo mais antigo e menos seguras usado nos domínios do Windows é NT LAN Manager (NTLM). Em casos em que o Kerberos não pode ser usado (normalmente fora de um domínio do Windows, como em um grupo de trabalho), o NTLM pode ser usado como uma alternativa. NTLM também está disponível como uma opção de segurança para o IIS.  
  
 Em um sistema Windows, a autorização funciona por meio da atribuição de cada computador e usuário para um conjunto de funções e grupos. Por exemplo, todos os computadores Windows devem configurar e controlado por uma pessoa (ou grupo de pessoas) na função do *administrador*. Outra função é que o *usuário*, que tem um conjunto muito mais restrito de permissões. Além da função, os usuários são atribuídos a grupos. Um grupo permite que vários usuários executar na mesma função. Na prática, portanto, uma máquina Windows é administrada, atribuindo usuários a grupos. Por exemplo, vários usuários podem ser atribuídos ao grupo de usuários de um computador e um conjunto muito mais restrito de usuários pode ser atribuído ao grupo de administradores. Em um computador local, um administrador também pode criar novos grupos e atribuir outros usuários (ou até mesmo outros grupos) ao grupo.  
  
 Em um computador executando o Windows, todas as pastas em um diretório podem ser protegida. Ou seja, você pode selecionar uma pasta e controlar quem pode acessar os arquivos, e se ou não pode copiar o arquivo ou (no caso mais privilegiado) alterar um arquivo, excluir um arquivo ou adicionar arquivos à pasta. Isso é conhecido como controle de acesso e o mecanismo para que ele é conhecido como a lista de controle de acesso (ACL). Ao criar o ACL, você pode atribuir privilégios de acesso a qualquer grupo ou grupos, bem como os membros individuais de um domínio.  
  
 A infraestrutura do WCF foi projetada para usar esses mecanismos de segurança do Windows. Portanto, se você estiver criando um serviço que é implantado em uma intranet, e cujos clientes são restringidos aos membros do domínio do Windows, a segurança é facilmente implementada. Somente os usuários válidos podem fazer logon no domínio. Depois que os usuários fazem logon, o controlador de Kerberos permite que cada usuário estabelecer contextos seguros com qualquer outro computador ou aplicativo. Em um computador local, grupos podem ser criados com facilidade e, ao proteger pastas específicas, esses grupos podem ser usados para atribuir privilégios de acesso no computador.  
  
## <a name="implementing-windows-security-on-intranet-services"></a>Implementar a segurança do Windows nos serviços da Intranet  
 Para proteger um aplicativo executado exclusivamente em um domínio do Windows, você pode usar as configurações de segurança padrão de qualquer um de <xref:System.ServiceModel.WSHttpBinding> ou o <xref:System.ServiceModel.NetTcpBinding> associação. Por padrão, qualquer pessoa no mesmo domínio do Windows pode acessar os serviços WCF. Como esses usuários fazer logon na rede, eles são confiáveis. As mensagens entre um serviço e um cliente são criptografadas para confidencialidade e integridade se inscreveu. Para obter mais informações sobre como criar um serviço que usa a segurança do Windows, consulte [como: proteger um serviço com credenciais do Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
### <a name="authorization-using-the-principalpermissionattribute-class"></a>Autorização usando a classe PrincipalPermissionAttribute  
 Se for necessário restringir o acesso de recursos em um computador, a maneira mais fácil é usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute> classe. Este atributo permite restringir a invocação de operações de serviço, exigindo que o usuário estar em um grupo do Windows especificado ou função, ou se um usuário específico. Para obter mais informações, consulte [como: restringir o acesso com a classe PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
### <a name="impersonation"></a>Representação  
 A representação é outro mecanismo que você pode usar para controlar o acesso aos recursos. Por padrão, um serviço hospedado pelo IIS será executado sob a identidade da conta ASPNET. A conta ASPNET pode acessar somente os recursos para os quais ele tem permissão. No entanto, é possível definir a ACL para uma pasta para excluir a conta de serviço do ASPNET, mas permitir que determinados outras identidades acessar a pasta. A pergunta, em seguida, torna-se como permitir que os usuários acessar a pasta se a conta ASPNET não tem permissão para fazer isso. A resposta é usar a representação, na qual o serviço pode usar as credenciais do cliente para acessar um recurso específico. Outro exemplo é ao acessar um banco de dados do SQL Server para que somente determinados usuários tem permissão. Para obter mais informações sobre como usar a representação, consulte [como: representar um cliente em um serviço](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md) e [delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="security-on-the-internet"></a>Segurança na Internet  
 Segurança na Internet consiste nos mesmos requisitos de segurança em uma intranet. Um serviço precisa apresentar suas credenciais para provar sua autenticidade e os clientes precisam provar sua identidade para o serviço. Depois que a identidade de um cliente está comprovada, o serviço pode controlar quanto o cliente tem a recursos de acesso. No entanto, devido à natureza heterogênea da Internet, as credenciais apresentadas são diferentes daqueles usados em um domínio do Windows. Enquanto que um controlador de Kerberos lida com a autenticação de usuários em um domínio com permissões para as credenciais, na Internet, serviços e clientes contam com qualquer uma das várias maneiras diferentes para apresentar as credenciais. No entanto, o objetivo deste tópico é apresentar uma abordagem comum que permite que você crie um serviço WCF que está acessível na Internet.  
  
### <a name="using-iis-and-aspnet"></a>Usando o IIS e ASP.NET  
 Os requisitos de segurança de Internet e os mecanismos para resolver esses problemas, não são novidade. O IIS é o servidor da Web da Microsoft para a Internet e tem muitos recursos de segurança que resolvem esses problemas; Além disso, [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] inclui recursos de segurança que os serviços WCF podem usar. Para tirar proveito desses recursos de segurança, hospede um serviço WCF no IIS.  
  
#### <a name="using-aspnet-membership-and-role-providers"></a>Usando provedores de função e associação do ASP.NET  
 O ASP.NET inclui um provedor de associação e funções. O provedor é um banco de dados de pares de nome/senha de usuário para autenticar chamadores que também permite que você especifique os privilégios de acesso do cada chamador. Com o WCF, você pode usar facilmente uma associação já existente e o provedor de função por meio da configuração. Para um aplicativo de exemplo que demonstra isso, consulte a [provedor de função e associação](../../../docs/framework/wcf/samples/membership-and-role-provider.md) exemplo.  
  
### <a name="credentials-used-by-iis"></a>Credenciais usadas pelo IIS  
 Ao contrário de um domínio do Windows apoiado por um controlador de Kerberos, a Internet é um ambiente sem um único controlador para gerenciar os milhões de usuários que fizerem logon qualquer momento. Em vez disso, as credenciais na Internet são geralmente na forma de certificados x. 509 (também conhecidos como certificados SSL, ou Secure Sockets Layer). Normalmente, esses certificados são emitidos por uma *autoridade de certificação*, que pode ser uma empresa de terceiros que atesta a autenticidade do certificado e a pessoa que ele tiver sido emitida para. Para expor seu serviço na Internet, você também deve fornecer um certificado confiável para autenticar seu serviço.  
  
 Surge a questão: neste ponto, como você obtém esse certificado? Uma abordagem é ir para uma autoridade de certificação de terceiros, como VeriSign, ou de Authenticode quando estiver pronto para implantar seu serviço e comprar um certificado para seu serviço. No entanto, se você estiver na fase de desenvolvimento com o WCF e ainda não está pronto para confirmar a compra de um certificado, ferramentas e técnicas existem para a criação de certificados X.509 que você pode usar para simular uma implantação de produção. Para obter mais informações, consulte [trabalhando com certificados](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="security-modes"></a>Modos de segurança  
 Programação de segurança do WCF envolve alguns pontos de decisão críticos. Um dos mais básica é a escolha da *modo de segurança*. Os dois modos de segurança principais são *modo de transporte* e *modo de mensagem*.  
  
 Um modo de terceiro, que combina a semântica de ambos os modos principais, está *transporte com modo de credenciais de mensagem*.  
  
 O modo de segurança determina como as mensagens são protegidas, e cada opção tem vantagens e desvantagens, conforme explicado abaixo. Para obter mais informações sobre como definir o modo de segurança, consulte [como: definir o modo de segurança](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
#### <a name="transport-mode"></a>Modo de transporte  
 Há várias camadas entre a rede e o aplicativo. Um deles é o *transporte* camada *,* que gerencia a transferência de mensagens entre pontos de extremidade. Para a finalidade de presente, ele só é necessário que você entenda que o WCF usa vários protocolos de transporte, cada um deles pode proteger a transferência de mensagens. (Para obter mais informações sobre os transportes, consulte [transportes](../../../docs/framework/wcf/feature-details/transports.md).)  
  
 Um protocolo comumente usado é HTTP; outra é TCP. Cada um desses protocolos pode proteger específica de transferência por um mecanismo (ou mecanismos) da mensagem para o protocolo. Por exemplo, o protocolo HTTP é protegido usando SSL sobre HTTP, frequentemente abreviado como "HTTPS". Assim, quando você seleciona o modo de transporte para segurança, você está escolhendo usar o mecanismo, conforme determinado pelo protocolo. Por exemplo, se você selecionar o <xref:System.ServiceModel.WSHttpBinding> de classe e definir seu modo de segurança de transporte, você está selecionando SSL sobre HTTP (HTTPS) como mecanismo de segurança. A vantagem do modo de transporte é que ele é mais eficiente do que o modo de mensagem porque a segurança é integrada em um nível relativamente baixo. Ao usar o modo de transporte, o mecanismo de segurança deve ser implementado de acordo com a especificação para o transporte e, portanto, as mensagens podem fluir com segurança apenas de ponto a ponto por meio do transporte.  
  
#### <a name="message-mode"></a>Modo de mensagem  
 Em contraste, o modo de mensagem fornece segurança, incluindo os dados de segurança como parte de cada mensagem. Usando XML e cabeçalhos de segurança SOAP, as credenciais e outros dados necessários para garantir que a integridade e a confidencialidade da mensagem são incluídos com todas as mensagens. Cada mensagem inclui dados de segurança, portanto, ele resulta em um pedágio sobre o desempenho porque cada mensagem deve ser processada individualmente. (No modo de transporte, depois que a camada de transporte é protegida, todas as mensagens de fluam livremente.) No entanto, a segurança de mensagem tem uma vantagem em relação a segurança de transporte: é mais flexível. Ou seja, os requisitos de segurança não são determinados pelo transporte. Você pode usar qualquer tipo de credencial de cliente para proteger a mensagem. (No modo de transporte, o protocolo de transporte determina o tipo de credencial de cliente que você pode usar).  
  
#### <a name="transport-with-message-credentials"></a>Transporte com as credenciais de mensagem  
 O terceiro modo combina o melhor de segurança de transporte e de mensagem. Nesse modo, a segurança de transporte é usada com eficiência, garantir a confidencialidade e integridade de cada mensagem. Ao mesmo tempo, cada mensagem inclui seus dados de credencial, o que permite que a mensagem a ser autenticada. Com a autenticação, autorização também pode ser implementada. Autenticando um remetente, acesso a recursos pode ser concedido (ou negado) de acordo com a identidade do remetente.  
  
## <a name="specifying-the-client-credential-type-and-credential-value"></a>Especificando o tipo de credencial de cliente e o valor de credencial  
 Depois de selecionar um modo de segurança, você talvez queira especificar um tipo de credencial de cliente. O tipo de credencial de cliente especifica o tipo de um cliente deve usar para se autenticar no servidor.  
  
 Nem todos os cenários exigem um tipo de credencial de cliente, no entanto. Usando SSL sobre HTTP (HTTPS), um serviço se autentica o cliente. Como parte desta autenticação, o certificado do serviço é enviado ao cliente em um processo chamado *negociação*. O transporte protegido por SSL garante que todas as mensagens são confidenciais.  
  
 Se você estiver criando um serviço que exige que o cliente seja autenticado, sua escolha de um tipo de credencial de cliente depende o transporte e o modo selecionado. Por exemplo, usando o transporte HTTP e escolhendo o modo de transporte fornece várias opções, como Basic, Digest e outros. (Para obter mais informações sobre esses tipos de credenciais, consulte [Noções básicas sobre a autenticação HTTP](../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).)  
  
 Se você estiver criando um serviço em um domínio do Windows que estará disponível somente para outros usuários da rede, mais fáceis de usar é o tipo de credencial de cliente do Windows. No entanto, você também precisará fornecer um serviço com um certificado. Isso é mostrado na [como: especificar valores de credencial de cliente](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
#### <a name="credential-values"></a>Valores de credenciais  
 Um *valor de credencial* é o serviço usa o valor real de credencial. Depois que você tiver especificado um tipo de credencial, você também precisará configurar seu serviço com as credenciais reais. Se você selecionou Windows (e o serviço será executado em um domínio do Windows), em seguida, você não especificar um valor de credencial real.  
  
## <a name="identity"></a>Identidade  
 No WCF, o termo *identidade* tem significados diferentes para o servidor e o cliente. Em suma, ao executar um serviço, uma identidade é atribuída ao contexto de segurança após a autenticação. Para exibir a identidade real, verifique as <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> propriedades do <xref:System.ServiceModel.ServiceSecurityContext> classe. Para obter mais informações, consulte [como: Examine o contexto de segurança](../../../docs/framework/wcf/how-to-examine-the-security-context.md).  
  
 Em contraste, no cliente, a identidade é usada para validar o serviço. Em tempo de design, um desenvolvedor cliente pode definir as [ \<identidade >](../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento para um valor obtido do serviço. Em tempo de execução, o cliente verifica o valor do elemento em relação a identidade real do serviço. Se a verificação falhar, o cliente encerra a comunicação. O valor pode ser um nome de usuário principal (UPN) se o serviço é executado sob a identidade de um usuário específico ou um nome de entidade de serviço (SPN) se o serviço é executado sob uma conta de computador. Para obter mais informações, consulte [identidade de serviço e autenticação](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md). A credencial também pode ser um certificado ou um campo localizado em um certificado que identifica o certificado.  
  
## <a name="protection-levels"></a>Níveis de proteção  
 O `ProtectionLevel` propriedade ocorre em várias classes de atributo (como o <xref:System.ServiceModel.ServiceContractAttribute> e o <xref:System.ServiceModel.OperationContractAttribute> classes). O nível de proteção é um valor que especifica se as mensagens (ou partes da mensagem) que dão suporte a um serviço estiver conectado, assinado e criptografado ou enviados sem criptografia ou assinaturas. Para obter mais informações sobre a propriedade, consulte [Noções básicas sobre nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md)e para exemplos de programação, consulte [como: definir a propriedade ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md). Para obter mais informações sobre como projetar um contrato de serviço com o `ProtectionLevel` no contexto, consulte [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Autenticação e identidade de serviço](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Noções básicas de nível de proteção](../../../docs/framework/wcf/understanding-protection-level.md)  
 [Delegação e representação](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Segurança](../../../docs/framework/wcf/feature-details/security.md)  
 [Visão geral de segurança](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Como definir a propriedade ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Como proteger um serviço com credenciais Windows](../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [Como definir o modo de segurança](../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [Como especificar o tipo de credencial do cliente](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)  
 [Como restringir o acesso com a classe PrincipalPermissionAttribute](../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Como representar um cliente em um serviço](../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)  
 [Como examinar o contexto de segurança](../../../docs/framework/wcf/how-to-examine-the-security-context.md)
