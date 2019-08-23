---
title: Substituindo a identidade de um serviço pela autenticação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: ec1acc009e58408fc41c60134538340486f19f75
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949670"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>Substituindo a identidade de um serviço pela autenticação
Normalmente, você não precisa definir a identidade em um serviço porque a seleção de um tipo de credencial de cliente determina o tipo de identidade exposto nos metadados do serviço. Por exemplo, o código de configuração a seguir usa o `clientCredentialType` [ \<elemento WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) e define o atributo como Windows.  

 O fragmento WSDL (Web Services Description Language) a seguir mostra a identidade do ponto de extremidade definido anteriormente. Neste exemplo, o serviço está sendo executado como um serviço hospedado automaticamente em uma conta de usuário específica (username@contoso.com) e, portanto, a identidade do nome UPN contém o nome da conta. O UPN também é conhecido como o nome de logon do usuário em um domínio do Windows.  

 Para obter um aplicativo de exemplo que demonstre a configuração de identidade, consulte [exemplo de identidade de serviço](../../../../docs/framework/wcf/samples/service-identity-sample.md). Para obter mais informações sobre a identidade do serviço, consulte [identidade e autenticação de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Autenticação e identidade Kerberos  
 Por padrão, quando um serviço é configurado para usar uma credencial do Windows [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) , um elemento de > de identidade que contém um [ \<elemento userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md) ou [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) é gerado no WSDL. Se o serviço estiver sendo executado sob `LocalSystem`a `LocalService`conta, `NetworkService` ou, um SPN (nome da entidade de serviço) é gerado por padrão na forma `host/`de nome de \< *host*> porque essas contas têm acesso ao os dados do SPN do computador. Se o serviço estiver sendo executado em uma conta diferente, Windows Communication Foundation (WCF) gerará um UPN na forma \<de *nome de usuário*>@<*nome_do_domínio*`>`. Isso ocorre porque a autenticação Kerberos requer que um UPN ou SPN seja fornecido ao cliente para autenticar o serviço.  
  
 Você também pode usar a ferramenta SetSPN. exe para registrar um SPN adicional com a conta de um serviço em um domínio. Você pode usar o SPN como a identidade do serviço. Para baixar a ferramenta, consulte [Windows 2000 Resource Kit Tool: Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752). Para obter mais informações sobre a ferramenta, consulte [visão geral do SetSPN](https://go.microsoft.com/fwlink/?LinkId=61374).  
  
> [!NOTE]
> Para usar o tipo de credencial do Windows sem negociação, a conta de usuário do serviço deve ter acesso ao SPN registrado com o domínio Active Directory. Você pode fazer isso das seguintes maneiras:  
  
- Use a conta NetworkService ou LocalSystem para executar o serviço. Como essas contas têm acesso ao SPN do computador que é estabelecido quando o computador ingressa no domínio Active Directory, o WCF gera automaticamente o elemento SPN apropriado dentro do ponto de extremidade do serviço nos metadados do serviço (WSDL).  
  
- Use uma conta de domínio Active Directory arbitrária para executar o serviço. Nesse caso, estabeleça um SPN para essa conta de domínio, que pode ser feito usando a ferramenta de utilitário SetSPN. exe. Depois de criar o SPN para a conta do serviço, configure o WCF para publicar esse SPN nos clientes do serviço por meio de seus metadados (WSDL). Isso é feito definindo a identidade do ponto de extremidade para o ponto de extremidade exposto, seja por meio de um código ou arquivo de configuração de aplicativo.  
  
 Para obter mais informações sobre SPNs, o protocolo Kerberos e Active Directory, consulte [complemento técnico Kerberos para Windows](https://go.microsoft.com/fwlink/?LinkId=88330).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Quando SPN ou UPN é igual à cadeia de caracteres vazia  
 Se você definir o SPN ou o UPN igual a uma cadeia de caracteres vazia, ocorrerá várias coisas diferentes, dependendo do nível de segurança e do modo de autenticação que está sendo usado:  
  
- Se você estiver usando a segurança de nível de transporte, a autenticação NT LanMan (NTLM) será escolhida.  
  
- Se você estiver usando a segurança em nível de mensagem, a autenticação poderá falhar, dependendo do modo de autenticação:  
  
- Se você estiver usando `spnego` o modo e `AllowNtlm` o atributo for definido `false`como, a autenticação falhará.  
  
- Se você estiver usando `spnego` o modo e `AllowNtlm` o atributo for definido `true`como, a autenticação falhará se o UPN estiver vazio, mas terá êxito se o SPN estiver vazio.  
  
- Se você estiver usando o Kerberos Direct (também conhecido como "One-shot"), a autenticação falhará.  
  
### <a name="using-the-identity-element-in-configuration"></a>Usando o \<elemento Identity > na configuração  
 Se você alterar o tipo de credencial do cliente na associação mostrada`,` anteriormente para o certificado, o WSDL gerado conterá um certificado X. 509 serializado na base64 para o valor de identidade, conforme mostrado no código a seguir. Esse é o padrão para todos os tipos de credencial do cliente que não sejam o Windows.  

 Você pode alterar o valor da identidade do serviço padrão ou alterar o tipo da identidade usando o elemento <`identity`> na configuração ou definindo a identidade no código. O código de configuração a seguir define uma identidade de DNS (sistema de nomes de `contoso.com`domínio) com o valor.  

### <a name="setting-identity-programmatically"></a>Definindo a identidade programaticamente  
 O serviço não precisa especificar uma identidade explicitamente, pois o WCF a determina automaticamente. No entanto, o WCF permite que você especifique uma identidade em um ponto de extremidade, se necessário. O código a seguir adiciona um novo ponto de extremidade de serviço com uma identidade DNS específica.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Como: Criar um verificador de identidade de cliente personalizado](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
