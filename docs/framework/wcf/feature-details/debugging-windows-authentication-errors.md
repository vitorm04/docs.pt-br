---
title: Depurando erros de autenticação do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: d9226324b69e5c27738abb35bb155a43964b9127
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495867"
---
# <a name="debugging-windows-authentication-errors"></a>Depurando erros de autenticação do Windows
Ao usar a autenticação do Windows como um mecanismo de segurança, a Interface de provedor de suporte de segurança (SSPI) gerencia os processos de segurança. Quando ocorrem erros de segurança na camada de SSPI, eles são apresentados pelo Windows Communication Foundation (WCF). Este tópico fornece uma estrutura e um conjunto de perguntas para ajudar a diagnosticar os erros.  
  
 Para obter uma visão geral do protocolo Kerberos, consulte [Kerberos explicado](http://go.microsoft.com/fwlink/?LinkID=86946); para obter uma visão geral de SSPI, consulte [SSPI](http://go.microsoft.com/fwlink/?LinkId=88941).  
  
 Para autenticação do Windows, o WCF normalmente usa o *Negotiate* segurança suporte Provider (SSP), que executa a autenticação mútua entre o cliente e o serviço Kerberos. Se o protocolo Kerberos não estiver disponível, por padrão, que o WCF reverterá para o NT LAN Manager (NTLM). No entanto, você pode configurar WCF para usar apenas o protocolo Kerberos (e lançar uma exceção se o Kerberos não estiver disponível). Você também pode configurar WCF para usar formulários restritos do protocolo Kerberos.  
  
## <a name="debugging-methodology"></a>Metodologia de depuração  
 O método básico é o seguinte:  
  
1.  Determine se você estiver usando autenticação do Windows. Se você estiver usando qualquer outro esquema, este tópico não se aplica.  
  
2.  Se tiver certeza de que você estiver usando autenticação do Windows, determine se a configuração do WCF usar direta de Kerberos ou Negotiate.  
  
3.  Depois de determinar se sua configuração está usando o protocolo Kerberos ou NTLM, você pode entender as mensagens de erro no contexto correto.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Disponibilidade do protocolo Kerberos e NTLM  
 O SSP do Kerberos requer um controlador de domínio para agir como Kerberos Key Distribution Center (KDC). O protocolo Kerberos está disponível somente quando o cliente e o serviço estiver usando identidades do domínio. Em outras combinações de conta, NTLM é usado, como resumido na tabela a seguir.  
  
 Os cabeçalhos da tabela mostram os tipos de conta possível usados pelo servidor. A coluna esquerda mostra os tipos possíveis de conta usados pelo cliente.  
  
||Usuário local|Sistema Local|Usuário de domínio|Máquina de domínio|  
|-|----------------|------------------|-----------------|--------------------|  
|Usuário local|NTLM|NTLM|NTLM|NTLM|  
|Sistema Local|NTLM anônimo|NTLM anônimo|NTLM anônimo|NTLM anônimo|  
|Usuário de domínio|NTLM|NTLM|Kerberos|Kerberos|  
|Máquina de domínio|NTLM|NTLM|Kerberos|Kerberos|  
  
 Especificamente, os quatro tipos de conta incluem:  
  
-   : Local somente máquina perfil de usuário. Por exemplo `MachineName\Administrator` ou `MachineName\ProfileName`.  
  
-   Sistema local: A conta interna sistema em um computador que não tenha ingressado em um domínio.  
  
-   Usuário de domínio: Uma conta de usuário em um domínio do Windows. Por exemplo: `DomainName\ProfileName`.  
  
-   Máquina de domínio: Um processo com a identidade da máquina executando em um computador que ingressou em um domínio do Windows. Por exemplo: `MachineName\Network Service`.  
  
> [!NOTE]
>  A credencial de serviço é capturada quando o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método o <xref:System.ServiceModel.ServiceHost> classe é chamada. A credencial do cliente é lida sempre que o cliente envia uma mensagem.  
  
## <a name="common-windows-authentication-problems"></a>Problemas comuns de autenticação do Windows  
 Esta seção aborda alguns problemas comuns de autenticação do Windows e as possíveis soluções.  
  
### <a name="kerberos-protocol"></a>Protocolo Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Problemas SPN/UPN com o protocolo Kerberos  
 Ao usar a autenticação do Windows e o protocolo é usado ou negociado por SSPI do Kerberos, a URL que usa o ponto de extremidade do cliente deve incluir o nome de domínio totalmente qualificado do host do serviço dentro da URL de serviço. Isso pressupõe que a conta sob a qual o serviço está sendo executado tem acesso para a chave de nome principal (SPN) de serviço do computador (padrão) que é criado quando o computador é adicionado ao domínio do Active Directory, que geralmente é feito através da execução do serviço no Conta de serviço de rede. Se o serviço não tiver acesso à chave SPN de máquina, você deve fornecer o correta SPN nome UPN ou (UPN) da conta sob a qual o serviço está em execução na identidade do ponto de extremidade do cliente. Para obter mais informações sobre o funcionamento do WCF com o SPN e UPN, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 No balanceamento de carga cenários, como Web farms ou ambientes Web, uma prática comum é definir uma conta exclusiva para cada aplicativo, atribua um SPN para essa conta, e certifique-se de que todos os serviços do aplicativo executados nessa conta.  
  
 Para obter um SPN para a conta de serviço, você precisa ser um administrador de domínio do Active Directory. Para obter mais informações, consulte [Kerberos suplemento técnico para Windows](http://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Direta do protocolo Kerberos requer que o serviço para execução em uma conta de computador do domínio  
 Isso ocorre quando o `ClientCredentialType` está definida como `Windows` e <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> está definida como `false`, conforme mostrado no código a seguir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Para corrigir, execute o serviço usando uma conta de máquina do domínio, como serviço de rede, em um domínio ingressou na máquina.  
  
### <a name="delegation-requires-credential-negotiation"></a>A delegação exige a negociação de credencial  
 Para usar o protocolo de autenticação Kerberos com delegação, você deve implementar o protocolo Kerberos com a negociação de credencial (às vezes chamada de "vários trecho" ou "várias etapas" Kerberos). Se você implementar a autenticação Kerberos sem negociação de credencial (às vezes chamada de "todos" ou "segmento único" Kerberos), uma exceção será lançada.  
  
 Para implementar o Kerberos com a negociação de credencial, siga as etapas a seguir:  
  
1.  Implementar a delegação definindo <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> para <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2.  Exigir negociação SSPI:  
  
    1.  Se você estiver usando associações padrão, defina o `NegotiateServiceCredential` propriedade `true`.  
  
    2.  Se você estiver usando associações personalizadas, definir o `AuthenticationMode` atributo do `Security` elemento `SspiNegotiated`.  
  
3.  Exigir a negociação de SSPI para usar o Kerberos, não permitindo o uso do NTLM:  
  
    1.  Faça isso no código, com a seguinte instrução: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  Ou você pode fazer isso no arquivo de configuração, definindo o `allowNtlm` atributo `false`. Esse atributo está contido no [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protocolo NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Negociar SSP cai para NTLM, mas NTLM está desabilitado  
 O <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> está definida como `false`, que faz com que o Windows Communication Foundation (WCF) para fazer um esforço para lançar uma exceção se NTLM é usado. Observe que a definição dessa propriedade `false` talvez não impeçam que as credenciais do NTLM seja enviado pela conexão.  
  
 O exemplo a seguir mostra como desabilitar o fallback para NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Falha de Logon NTLM  
 As credenciais do cliente não são válidas no serviço. Verifique se o nome de usuário e a senha estão definidas corretamente e correspondem a uma conta que é conhecida para o computador onde o serviço está em execução. NTLM usa as credenciais especificadas para fazer logon no computador do serviço. Enquanto as credenciais podem ser válidas no computador onde o cliente está sendo executado, esse logon falhará se as credenciais não são válidas no computador do serviço.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Logon anônimo NTLM ocorre, mas são de Logons anônimo é desabilitado por padrão  
 Ao criar um cliente, o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> está definida como <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, conforme mostrado no exemplo a seguir, mas, por padrão, o servidor não permite logons anônimos. Isso ocorre porque o valor padrão de <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> propriedade do <xref:System.ServiceModel.Security.WindowsServiceCredential> classe é `false`.  
  
 O seguinte código de cliente tenta ativar logons anônimos (Observe que a propriedade padrão é `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 O código de serviço a seguir altera o padrão para habilitar logons anônimos pelo servidor.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Para obter mais informações sobre representação, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Como alternativa, o cliente está sendo executado como um serviço do Windows, usando a conta interna do sistema.  
  
### <a name="other-problems"></a>Outros problemas  
  
#### <a name="client-credentials-are-not-set-correctly"></a>As credenciais do cliente não estão definidas corretamente  
 Usa a autenticação do Windows a <xref:System.ServiceModel.Security.WindowsClientCredential> instância retornada pelo <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade do <xref:System.ServiceModel.ClientBase%601> classe, não o <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. O exemplo a seguir mostra um exemplo incorreto.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 O exemplo a seguir mostra o exemplo correto.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>SSPI não está disponível  
 Os seguintes sistemas operacionais têm suporte quando usado como um servidor de autenticação do Windows: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition, e [!INCLUDE[wv](../../../../includes/wv-md.md)]inicial edições.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Desenvolvimento e implantação com diferentes identidades  
 Se você desenvolve seu aplicativo em um computador e implanta em outro e usa diferentes tipos de conta para autenticar em cada computador, você pode enfrentar um comportamento diferente. Por exemplo, suponha que você desenvolve seu aplicativo em um computador Windows XP Pro usando o `SSPI Negotiated` modo de autenticação. Se você usar uma conta de usuário local para autenticação, protocolo NTLM será usado. Depois que o aplicativo é desenvolvido, implante o serviço em uma máquina Windows Server 2003 onde ele é executado sob uma conta de domínio. Agora o cliente não será capaz de autenticar o serviço porque ele irá usar o Kerberos e um controlador de domínio.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
