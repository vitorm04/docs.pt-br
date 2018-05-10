---
title: Substituindo a identidade de um serviço pela autenticação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 3df1f2490f8636d52ac75fad2469adadec2a57da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Substituindo a identidade de um serviço pela autenticação
Normalmente, você não precisa definir a identidade de um serviço porque a seleção de um tipo de credencial de cliente determina o tipo de identidade exposto nos metadados do serviço. Por exemplo, o código de configuração a seguir usa o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento e define o `clientCredentialType` de atributo para o Windows.  
  
  
  
 O fragmento de WSDL Web Services Description Language () a seguir mostra a identidade do ponto de extremidade definida anteriormente. Neste exemplo, o serviço está em execução como um serviço auto-hospedado sob uma conta de usuário específica (username@contoso.com) e, portanto, a identidade do usuário principal (UPN) do nome contém o nome da conta. O UPN é também conhecido como o nome de logon do usuário em um domínio do Windows.  
  
  
  
 Para um aplicativo de exemplo que mostra a configuração de identidade, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md). Para obter mais informações sobre a identidade de serviço, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Identidade e autenticação Kerberos  
 Por padrão, quando um serviço é configurado para usar uma credencial do Windows, um [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento que contém um [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) ou [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemento é gerado no WSDL. Se o serviço está em execução sob o `LocalSystem`, `LocalService`, ou `NetworkService` conta, um serviço (SPN) nome da entidade é gerado por padrão na forma de `host/` \< *hostname*> porque Essas contas têm acesso aos dados SPN do computador. Se o serviço está em execução em uma conta diferente, o Windows Communication Foundation (WCF) gera um UPN no formato \< *username*>@<*domainName* `>` . Isso ocorre porque a autenticação Kerberos requer que um UPN ou um SPN fornecido ao cliente para autenticar o serviço.  
  
 Você também pode usar a ferramenta Setspn.exe para registrar um SPN adicional com uma conta de serviço em um domínio. Você pode usar o SPN como a identidade do serviço. Para baixar a ferramenta, consulte [Windows 2000 Resource Kit Tool: Setspn.exe](http://go.microsoft.com/fwlink/?LinkId=91752). Para obter mais informações sobre a ferramenta, consulte [visão geral do Setspn](http://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Para usar o tipo de credencial do Windows sem negociação, a conta de usuário do serviço deve ter acesso para o SPN está registrado com o domínio do Active Directory. Você pode fazer isso das seguintes maneiras:  
  
-   Use a conta NetworkService ou LocalSystem para executar o serviço. Como essas contas têm acesso à máquina SPN é estabelecida quando o computador ingressa no domínio do Active Directory, o WCF gera automaticamente o elemento SPN apropriado dentro do ponto de extremidade do serviço nos metadados do serviço (WSDL).  
  
-   Use uma conta de domínio do Active Directory arbitrária para executar o serviço. Nesse caso, estabeleça um SPN para essa conta de domínio, que pode ser feito usando a ferramenta Setspn.exe. Depois de criar o SPN para a conta de serviço, configure WCF para publicar esse SPN para clientes do serviço por meio de seus metadados (WSDL). Isso é feito definindo-se a identidade do ponto de extremidade para o ponto de extremidade exposto, por meio de um arquivo de configuração do aplicativo ou código.  
  
 Para obter mais informações sobre SPNs, o protocolo Kerberos e o Active Directory, consulte [Kerberos suplemento técnico para Windows](http://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Quando SPN ou UPN é igual a cadeia de caracteres vazia  
 Se você definir o SPN ou UPN igual a uma cadeia de caracteres vazia, várias coisas diferentes acontecem, dependendo do modo de autenticação e nível de segurança que está sendo usado:  
  
-   Se você estiver usando a segurança em nível de transporte, autenticação NT LanMan (NTLM) é escolhida.  
  
-   Se você estiver usando a segurança em nível de mensagem, a autenticação pode falhar, dependendo do modo de autenticação:  
  
-   Se você estiver usando `spnego` modo e o `AllowNtlm` atributo é definido como `false`, falha de autenticação.  
  
-   Se você estiver usando `spnego` modo e o `AllowNtlm` atributo é definido como `true`, a autenticação falhará se o UPN está vazio, mas terá êxito se o SPN está vazio.  
  
-   Se você estiver usando o Kerberos diretamente (também conhecido como "todos"), a autenticação falhará.  
  
### <a name="using-the-identity-element-in-configuration"></a>Usando o \<identidade > elemento na configuração  
 Se você alterar o tipo de credencial de cliente na associação mostrada anteriormente ao certificado`,` , em seguida, o WSDL gerado contém uma Base64 serializado certificado x. 509 para o valor de identidade, conforme mostrado no código a seguir. Esse é o padrão para todos os tipos de credencial de cliente diferentes do Windows.  
  
  
  
 Você pode alterar o valor da identidade do serviço padrão ou alterar o tipo de identidade usando o <`identity`> elemento na configuração ou definindo a identidade no código. O código de configuração a seguir define uma identidade do DNS (sistema) do nome de domínio com o valor `contoso.com`.  
  
  
  
### <a name="setting-identity-programmatically"></a>Definir a identidade por meio de programação  
 Seu serviço não precisa especificar explicitamente uma identidade, pois WCF determina automaticamente. No entanto, o WCF permite que você especifique uma identidade em um ponto de extremidade, se necessário. O código a seguir adiciona um novo ponto de extremidade de serviço com uma identidade específica de DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um verificador de identidade de cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
