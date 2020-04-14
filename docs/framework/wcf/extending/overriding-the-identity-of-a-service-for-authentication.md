---
title: Substituindo a identidade de um serviço pela autenticação
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: 5649ef4cc05c9c16b1f8f626ba5e2e584b0e52eb
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278906"
---
# <a name="override-the-identity-of-a-service-for-authentication"></a>Anular a identidade de um serviço de autenticação

Normalmente, você não precisa definir a identidade em um serviço porque a seleção de um tipo de credencial do cliente dita o tipo de identidade exposta nos metadados do serviço. Por exemplo, o código de configuração a seguir `clientCredentialType` usa o [ \<elemento wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) e define o atributo para o Windows.  

 O fragmento de WSDL (Web Services Description Language, linguagem de descrição dos serviços da Web) a seguir mostra a identidade do ponto final previamente definido. Neste exemplo, o serviço está sendo executado como um serviçousername@contoso.comauto-hospedado em uma determinada conta de usuário ( ) e, portanto, a identidade do nome principal do usuário (UPN) contém o nome da conta. O UPN também é conhecido como o nome de login do usuário em um domínio do Windows.  

 Para obter um aplicativo de exemplo que demonstre a configuração de identidade, consulte [Amostra de identidade de serviço](../samples/service-identity-sample.md). Para obter mais informações sobre a identidade do serviço, consulte [Identidade de Serviço e Autenticação](../feature-details/service-identity-and-authentication.md).  
  
## <a name="kerberos-authentication-and-identity"></a>Autenticação e Identidade kerberos  
 Por padrão, quando um serviço é configurado para [ \<](../../configure-apps/file-schema/wcf/identity.md) usar uma credencial do Windows, um elemento de>de identidade que contém um [ \<>de usuárioPrincipalName](../../configure-apps/file-schema/wcf/userprincipalname.md) ou [ \<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) elemento é gerado no WSDL. Se o serviço estiver `LocalSystem` `LocalService`sendo `NetworkService` executado sob o , ou conta, um nome principal `host/` \<de serviço (SPN) é gerado por padrão na forma de *hostname*> porque essas contas têm acesso aos dados SPN do computador. Se o serviço estiver sendo executado em outra conta, o Windows Communication \<Foundation (WCF) gerará um UPN na forma de nome de *usuário*>@<*nome de usoNome*`>`. Isso ocorre porque a autenticação kerberos exige que uma UPN ou SPN seja fornecida ao cliente para autenticar o serviço.  
  
 Você também pode usar a ferramenta [Setspn](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731241(v=ws.10)?redirectedfrom=MSDN) para registrar um SPN adicional com a conta de um serviço em um domínio. Em seguida, você pode usar o SPN como a identidade do serviço. Para obter mais informações sobre a ferramenta, consulte [Setspn Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).  
  
> [!NOTE]
> Para usar o tipo de credencial do Windows sem negociação, a conta de usuário do serviço deve ter acesso ao SPN que está registrado no domínio Active Directory. Você pode fazer isso das seguintes maneiras:  
  
- Use a conta NetworkService ou LocalSystem para executar seu serviço. Como essas contas têm acesso à máquina SPN que é estabelecida quando a máquina entra no domínio active Directory, o WCF gera automaticamente o elemento SPN adequado dentro do ponto final do serviço nos metadados do serviço (WSDL).  
  
- Use uma conta de domínio do Active Directory arbitrária para executar seu serviço. Neste caso, estabeleça um SPN para essa conta de domínio, o que você pode fazer usando a ferramenta utilitário Setspn.exe. Depois de criar o SPN para a conta do serviço, configure o WCF para publicar esse SPN para os clientes do serviço através de seus metadados (WSDL). Isso é feito definindo a identidade de ponto final para o ponto final exposto, seja através de um arquivo de configuração de aplicativo ou código.  
  
 Para obter mais informações sobre SPNs, o protocolo Kerberos e o Active Directory, consulte [O Suplemento Técnico kerberos para Windows](https://docs.microsoft.com/previous-versions/msp-n-p/ff649429(v=pandp.10)).  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>Quando SPN ou UPN iguala a cadeia de string vazia  
 Se você definir o SPN ou UPN igual a uma seqüência de string vazia, uma série de coisas diferentes acontecerão, dependendo do nível de segurança e do modo de autenticação que está sendo usado:  
  
- Se você estiver usando a segurança do nível de transporte, a autenticação NT LanMan (NTLM) será escolhida.  
  
- Se você estiver usando a segurança do nível de mensagem, a autenticação pode falhar, dependendo do modo de autenticação:  
  
- Se você `spnego` estiver usando `AllowNtlm` o modo `false`e o atributo estiver definido como, a autenticação falhará.  
  
- Se você `spnego` estiver usando `AllowNtlm` o modo `true`e o atributo estiver definido como, a autenticação falhará se o UPN estiver vazio, mas será bem sucedido se o SPN estiver vazio.  
  
- Se você estiver usando o Kerberos direct (também conhecido como "one-shot"), a autenticação falhará.  
  
### <a name="use-the-identity-element-in-configuration"></a>Use \<o elemento de> de identidade na configuração  
 Se você alterar o tipo de credencial do `Certificate`cliente na vinculação mostrada anteriormente, então o WSDL gerado contém um certificado X.509 serializado Base64 para o valor de identidade mostrado no código a seguir. Este é o padrão para todos os tipos de credenciais do cliente que não seja o Windows.  

 Você pode alterar o valor da identidade de serviço padrão ou `identity` alterar o tipo da identidade usando o elemento> <na configuração ou definindo a identidade em código. O código de configuração a seguir define uma `contoso.com`identidade de dns (domain name system) com o valor .  

### <a name="set-identity-programmatically"></a>Definir identidade programática  
 Seu serviço não precisa especificar explicitamente uma identidade, porque o WCF a determina automaticamente. No entanto, o WCF permite que você especifique uma identidade em um ponto final, se necessário. O código a seguir adiciona um novo ponto final de serviço com uma identidade DNS específica.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>Confira também

- [Como criar um verificador de identidade de cliente personalizado](how-to-create-a-custom-client-identity-verifier.md)
- [Identidade e autenticação de serviço](../feature-details/service-identity-and-authentication.md)
