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
ms.openlocfilehash: 28c70ca860083808c93fa58b498e22ea4e4ca6cb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299443"
---
# <a name="debugging-windows-authentication-errors"></a>Depurando erros de autenticação do Windows
Ao usar a autenticação do Windows como um mecanismo de segurança, a Interface de provedor de suporte de segurança (SSPI) lida com processos de segurança. Quando ocorrem erros de segurança na camada de SSPI, elas são exibidas pelo Windows Communication Foundation (WCF). Este tópico fornece uma estrutura e um conjunto de perguntas para ajudar a diagnosticar os erros.  
  
 Para obter uma visão geral do protocolo Kerberos, consulte [Kerberos explicado](https://go.microsoft.com/fwlink/?LinkID=86946); para uma visão geral de SSPI, consulte [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).  
  
 Para a autenticação do Windows, o WCF normalmente usa o *Negotiate* segurança suporte SSP (provedor), que executa a autenticação mútua entre o cliente e o serviço Kerberos. Se o protocolo Kerberos não estiver disponível, por padrão, que o WCF pode fazer fallback para o NT LAN Manager (NTLM). No entanto, você pode configurar o WCF para usar apenas o protocolo Kerberos (e para gerar uma exceção se o Kerberos não estiver disponível). Você também pode configurar o WCF para usar formulários restritos do protocolo Kerberos.  
  
## <a name="debugging-methodology"></a>Metodologia de depuração  
 O método básico é o seguinte:  
  
1. Determine se você estiver usando a autenticação do Windows. Se você estiver usando qualquer outro esquema, este tópico não se aplica.  
  
2. Se você estiver se que você estiver usando a autenticação do Windows, determine se a configuração do WCF usa direta de Kerberos ou Negotiate.  
  
3. Depois de determinar se sua configuração está usando o protocolo Kerberos ou NTLM, você pode entender mensagens de erro no contexto correto.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Disponibilidade do protocolo Kerberos e NTLM  
 O SSP do Kerberos requer um controlador de domínio para agir como o Centro de distribuição de chave de Kerberos (KDC). O protocolo Kerberos está disponível somente quando o cliente e o serviço estiver usando identidades de domínio. Em outras combinações de conta, NTLM é usado, conforme resumido na tabela a seguir.  
  
 Os cabeçalhos de tabela mostram os tipos possíveis de conta usados pelo servidor. A coluna esquerda mostra os tipos possíveis de conta usados pelo cliente.  
  
||Usuário local|Sistema Local|Domain User|Domain Machine|  
|-|----------------|------------------|-----------------|--------------------|  
|Usuário local|NTLM|NTLM|NTLM|NTLM|  
|Sistema Local|NTLM anônimo|NTLM anônimo|NTLM anônimo|NTLM anônimo|  
|Domain User|NTLM|NTLM|Kerberos|Kerberos|  
|Domain Machine|NTLM|NTLM|Kerberos|Kerberos|  
  
 Especificamente, os quatro tipos de conta incluem:  
  
-   Usuário local: Perfil de usuário somente na máquina. Por exemplo `MachineName\Administrator` ou `MachineName\ProfileName`.  
  
-   Sistema local: A conta interna sistema em um computador que não ingressou em um domínio.  
  
-   Usuário de domínio: Uma conta de usuário em um domínio do Windows. Por exemplo: `DomainName\ProfileName`.  
  
-   Domain Machine: Um processo com a identidade da máquina em execução em um computador ingressado em um domínio do Windows. Por exemplo: `MachineName\Network Service`.  
  
> [!NOTE]
>  A credencial de serviço é capturada quando o <xref:System.ServiceModel.ICommunicationObject.Open%2A> método da <xref:System.ServiceModel.ServiceHost> classe é chamada. A credencial do cliente é lida sempre que o cliente envia uma mensagem.  
  
## <a name="common-windows-authentication-problems"></a>Problemas comuns de autenticação do Windows  
 Esta seção aborda alguns problemas comuns de autenticação do Windows e as possíveis soluções.  
  
### <a name="kerberos-protocol"></a>Protocolo Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Problemas SPN/UPN com o protocolo Kerberos  
 Ao usar autenticação do Windows e o Kerberos protocolo é usado ou negociado pelo SSPI, a URL que usa o ponto de extremidade do cliente deve incluir o nome de domínio totalmente qualificado do host do serviço dentro da URL de serviço. Isso pressupõe que a conta sob a qual o serviço está em execução tem acesso à chave de nome principal (SPN) de serviço de máquina (padrão) que é criado quando o computador é adicionado ao domínio do Active Directory, que geralmente é feito pela execução do serviço no Conta de serviço de rede. Se o serviço não tiver acesso à chave SPN de máquina, você deve fornecer o correta SPN nome UPN ou (UPN) da conta sob a qual o serviço está em execução na identidade do ponto de extremidade do cliente. Para obter mais informações sobre o funcionamento do WCF com o SPN e UPN, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 No balanceamento de carga cenários, como farms da Web ou ambientes Web, uma prática comum é definir uma conta exclusiva para cada aplicativo, atribua um SPN para essa conta e certifique-se de que todos os serviços do aplicativo é executado nessa conta.  
  
 Para obter um SPN para a conta do serviço, você precisa ser um administrador de domínio do Active Directory. Para obter mais informações, consulte [Kerberos técnica suplementar para Windows](https://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Direta do protocolo Kerberos requer o serviço para execução em uma conta de computador do domínio  
 Isso ocorre quando o `ClientCredentialType` estiver definida como `Windows` e o <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> estiver definida como `false`, conforme mostrado no código a seguir.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Para corrigir, execute o serviço usando uma conta de computador do domínio como o serviço de rede, em um domínio ingressado no computador.  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegação exige a negociação de credencial  
 Para usar o protocolo de autenticação Kerberos com delegação, você deve implementar o protocolo Kerberos com negociação de credencial (às vezes chamada de "multi-segmentos" ou "várias etapas" Kerberos). Se você implementar a autenticação Kerberos sem negociação de credencial (às vezes chamada de "todos" ou "segmento único" Kerberos), uma exceção será lançada.  
  
 Para implementar o Kerberos com a negociação de credencial, execute as seguintes etapas:  
  
1. Implementar a delegação, definindo <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> para <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2. Exigir a negociação SSPI:  
  
    1.  Se você estiver usando associações padrão, defina as `NegotiateServiceCredential` propriedade para `true`.  
  
    2.  Se você estiver usando associações personalizadas, defina a `AuthenticationMode` atributo o `Security` elemento a ser `SspiNegotiated`.  
  
3. Exigir a negociação SSPI para usar o Kerberos, não permitindo o uso do NTLM:  
  
    1.  Para fazer isso no código, com a seguinte instrução: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  Ou você pode fazer isso no arquivo de configuração, definindo o `allowNtlm` atributo `false`. Esse atributo está contido na [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protocolo NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Negociar SSP cai para NTLM, mas o NTLM está desabilitado  
 O <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> estiver definida como `false`, que faz com que o Windows Communication Foundation (WCF) para fazer um esforço para lançar uma exceção se NTLM for usado. Observe que a definição dessa propriedade `false` talvez não impeçam que as credenciais do NTLM sejam enviados durante a transmissão.  
  
 O exemplo a seguir mostra como desabilitar o fallback para NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Falha de Logon NTLM  
 As credenciais do cliente não são válidas no serviço. Verifique se o nome de usuário e senha estão definidas corretamente e correspondem a uma conta que é conhecida como o computador onde o serviço está em execução. NTLM usa as credenciais especificadas para fazer logon no computador do serviço. Enquanto as credenciais podem ser válidas no computador onde o cliente está em execução, esse logon falhará se as credenciais não são válidas no computador do serviço.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Logon anônimo NTLM ocorre, mas são de Logons anônimo é desabilitado por padrão  
 Durante a criação de um cliente, o <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> estiver definida como <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, conforme mostrado no exemplo a seguir, mas por padrão, o servidor não permite logons anônimos. Isso ocorre porque o valor padrão a <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> propriedade do <xref:System.ServiceModel.Security.WindowsServiceCredential> classe é `false`.  
  
 O seguinte código de cliente tenta ativar logons anônimos (Observe que a propriedade padrão é `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 O código de serviço a seguir altera o padrão para habilitar logons anônimos pelo servidor.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Para obter mais informações sobre representação, consulte [delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Como alternativa, o cliente está em execução como um serviço do Windows, usando a conta interna do sistema.  
  
### <a name="other-problems"></a>Outros problemas  
  
#### <a name="client-credentials-are-not-set-correctly"></a>As credenciais do cliente não estão definidas corretamente  
 A autenticação do Windows usa o <xref:System.ServiceModel.Security.WindowsClientCredential> instância retornada pela <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade da <xref:System.ServiceModel.ClientBase%601> classe, não o <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. O exemplo a seguir mostra um exemplo de incorreto.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 A seguir mostra o exemplo correto.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>SSPI não está disponível  
 Os seguintes sistemas operacionais não têm suporte quando usado como um servidor de autenticação do Windows: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition, e [!INCLUDE[wv](../../../../includes/wv-md.md)]Home editions.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Desenvolvendo e implantando com identidades diferentes  
 Se você desenvolve seu aplicativo em um computador e implantar em outro e usa diferentes tipos de conta para autenticar em cada computador, você pode enfrentar um comportamento diferente. Por exemplo, suponha que você desenvolve seu aplicativo em um computador Windows XP Pro usando o `SSPI Negotiated` modo de autenticação. Se você usar uma conta de usuário local para autenticar com o, protocolo NTLM será usado. Depois que o aplicativo é desenvolvido, você implantar o serviço a uma máquina Windows Server 2003 onde ele é executado sob uma conta de domínio. Neste ponto o cliente não será capaz de autenticar o serviço, pois ele estará usando Kerberos e um controlador de domínio.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Delegação e representação](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
