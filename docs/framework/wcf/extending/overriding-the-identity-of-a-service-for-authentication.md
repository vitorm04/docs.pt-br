---
title: Substituindo a identidade de um serviço pela autenticação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: a5a32220ad1f638bf2e93051e9b436d8270aec2f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082185"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Substituindo a identidade de um serviço pela autenticação
Normalmente, você não precisa definir a identidade em um serviço, pois a seleção de um tipo de credencial de cliente determina o tipo de identidade exposto nos metadados de serviço. Por exemplo, o código de configuração a seguir usa o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elemento e define o `clientCredentialType` de atributo para Windows.  

 O fragmento de descrição linguagem WSDL (Web Services) a seguir mostra a identidade para o ponto de extremidade definido anteriormente. Neste exemplo, o serviço é executado como um serviço auto-hospedado em uma conta de usuário específico (username@contoso.com) e, portanto, a identidade de nome principal (UPN) do usuário contém o nome da conta. O UPN é também conhecido como o nome de logon do usuário em um domínio do Windows.  

 Para um aplicativo de exemplo que demonstra a configuração de identidade, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md). Para obter mais informações sobre a identidade de serviço, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Identidade e autenticação Kerberos  
 Por padrão, quando um serviço é configurado para usar uma credencial do Windows, uma [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento que contém um [ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) ou [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemento é gerado no WSDL. Se o serviço está sendo executado o `LocalSystem`, `LocalService`, ou `NetworkService` conta, um serviço (SPN) nome da entidade é gerado por padrão na forma de `host/` \< *hostname*> porque Essas contas tenham acesso aos dados SPN do computador. Se o serviço está em execução em uma conta diferente, o Windows Communication Foundation (WCF) gera um UPN no formato \< *nome de usuário*>@<*domainName* `>` . Isso ocorre porque a autenticação Kerberos requer que um nome UPN ou um SPN fornecido ao cliente para autenticar o serviço.  
  
 Você também pode usar a ferramenta Setspn.exe para registrar um SPN adicional com uma conta de serviço em um domínio. Em seguida, você pode usar o SPN como a identidade do serviço. Para baixar a ferramenta, consulte [ferramenta do Windows 2000 Resource Kit: Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752). Para obter mais informações sobre a ferramenta, consulte [visão geral do Setspn](https://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
>  Para usar o tipo de credencial do Windows sem negociação, a conta de usuário do serviço deve ter acesso para o SPN está registrado com o domínio do Active Directory. Você pode fazer isso das seguintes maneiras:  
  
-   Use a conta NetworkService ou LocalSystem para executar seu serviço. Como essas contas têm acesso ao computador do SPN é estabelecido quando o computador ingressa no domínio do Active Directory, o WCF gera automaticamente o elemento SPN apropriado dentro do ponto de extremidade de serviço nos metadados do serviço (WSDL).  
  
-   Use uma conta de domínio do Active Directory arbitrária para executar seu serviço. Nesse caso, estabelece um SPN para essa conta de domínio, que pode ser feito usando a ferramenta de utilitário Setspn.exe. Depois de criar o SPN para a conta de serviço, configure o WCF para publicar esse SPN aos clientes do serviço por meio de seus metadados (WSDL). Isso é feito definindo a identidade do ponto de extremidade para o ponto de extremidade exposto, por meio de um arquivo de configuração de aplicativo ou código.  
  
 Para obter mais informações sobre SPNs, o protocolo Kerberos e do Active Directory, consulte [Kerberos técnica suplementar para Windows](https://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Quando SPN ou UPN é igual a cadeia de caracteres vazia  
 Se você definir o SPN ou UPN igual a uma cadeia de caracteres vazia, uma série de coisas diferentes acontece, dependendo do modo de autenticação e nível de segurança que está sendo usado:  
  
-   Se você estiver usando a segurança em nível de transporte, autenticação NT LanMan (NTLM) será escolhida.  
  
-   Se você estiver usando a segurança em nível de mensagem, a autenticação pode falhar, dependendo do modo de autenticação:  
  
-   Se você estiver usando `spnego` modo e o `AllowNtlm` atributo é definido como `false`, falha de autenticação.  
  
-   Se você estiver usando `spnego` modo e o `AllowNtlm` atributo é definido como `true`, a autenticação falhará se o UPN está vazio, mas terá êxito se o SPN está vazio.  
  
-   Se você estiver usando o Kerberos direto (também conhecido como "monoestável"), a autenticação falhará.  
  
### <a name="using-the-identity-element-in-configuration"></a>Usando o \<identidade > elemento na configuração  
 Se você alterar o tipo de credencial de cliente na associação mostrada anteriormente ao certificado`,` WSDL gerado contém uma Base64 serializada certificado x. 509 para o valor de identidade, conforme mostrado no código a seguir. Esse é o padrão para todos os tipos de credencial de cliente que não sejam Windows.  

 Você pode alterar o valor de identidade do serviço padrão ou alterar o tipo de identidade usando o <`identity`> elemento na configuração ou definindo a identidade no código. O código de configuração a seguir define uma identidade do DNS (sistema) do nome de domínio com o valor `contoso.com`.  

### <a name="setting-identity-programmatically"></a>Definindo a identidade do forma programática  
 Seu serviço não precisa especificar explicitamente uma identidade, porque o WCF determina automaticamente. No entanto, o WCF permite que você especifique uma identidade de um ponto de extremidade, se necessário. O código a seguir adiciona um novo ponto de extremidade de serviço com uma identidade específica do DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Como: criar um verificador de identidade de cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Identidade e autenticação de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
