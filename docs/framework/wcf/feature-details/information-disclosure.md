---
title: Divulgação de informações
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 0e45a71855ecb172f36aae8139f89d4b8c8ffd0d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425302"
---
# <a name="information-disclosure"></a>Divulgação de informações

Divulgação de informações permite que um invasor obtenha informações valiosas sobre um sistema. Portanto, sempre considere quais informações você está revelando e se ele pode ser usado por um usuário mal-intencionado. A seguir lista os ataques de divulgação de informações possíveis e fornece atenuações para cada um.

## <a name="message-security-and-http"></a>HTTP e a segurança de mensagem

Se você estiver usando a segurança em nível de mensagem sobre uma camada de transporte HTTP, lembre-se de que a segurança em nível de mensagem não protege cabeçalhos HTTP. A única maneira de proteger os cabeçalhos HTTP é usar o transporte HTTPS em vez de HTTP. Transporte HTTPS faz com que a mensagem inteira, incluindo os cabeçalhos HTTP, para serem criptografados usando o protocolo Secure Sockets Layer (SSL).

## <a name="policy-information"></a>Informações de política

Manter a política de segurança é importante, especialmente em cenários de Federação em que os requisitos de token emitido confidenciais ou informações de emissor de token são expostas na política. Nesses casos, a recomendação é proteger o ponto de extremidade de serviço federado diretiva para impedir que invasores obter informações sobre o serviço, como o tipo de declarações para colocar no token emitido, ou redirecionando os clientes para mal-intencionado emissores de token. Por exemplo, um invasor poderia descobrir os pares de nome/senha de usuário reconfigurando a cadeia de confiança federada para terminar em um emissor que executou um ataque man-in-the-middle. Também é recomendável que verifique se os clientes federados que obtêm suas associações por meio da recuperação de política que confiar os emissores na cadeia de confiança federada obtido. Para obter mais informações sobre cenários de federação, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).

## <a name="memory-dumps-can-reveal-claim-information"></a>Despejos de memória podem revelar informações de declaração

Quando um aplicativo falhar, arquivos de log, como aqueles gerados por recuperação de desastre. Watson, pode conter as informações de declaração. Essas informações não devem ser exportadas para outras entidades, como as equipes de suporte; Caso contrário, as informações de declaração que contém dados particulares também são exportadas. Você pode mitigar isso por não enviar os arquivos de log para entidades desconhecidas. Para obter mais informações, consulte [Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=89160).

## <a name="endpoint-addresses"></a>Endereços do ponto de extremidade

Um endereço de ponto de extremidade contém as informações necessárias para se comunicar com um ponto de extremidade. Segurança SOAP deve incluir o endereço completo em que as mensagens de negociação de segurança que são trocadas para negociar uma chave simétrica entre um cliente e um servidor. Como negociação de segurança é um processo de inicialização, os cabeçalhos de endereço não podem ser criptografados durante esse processo. Portanto, o endereço não deve conter todos os dados confidenciais; Caso contrário, isso leva a ataques de divulgação de informações.

## <a name="certificates-transferred-unencrypted"></a>Certificados transferidos não criptografada

Quando você usa um certificado x. 509 para autenticar um cliente, o certificado é transferido de modo transparente, dentro do cabeçalho SOAP. Lembre-se de que isso como uma potencial divulgação de informações de identificação pessoal (PII). Isso não é um problema para `TransportWithMessageCredential` modo, em que a mensagem inteira é criptografada com segurança em nível de transporte.

## <a name="service-references"></a>Referências de serviço

Uma referência de serviço é uma referência a outro serviço. Por exemplo, um serviço pode passar uma referência a um cliente durante uma operação de serviço. A referência de serviço também é usada com um *Verificador de identidade de confiança*, um componente interno que garante a identidade da entidade de destino antes da divulgação de informações como dados de aplicativo ou as credenciais para o destino. Se a identidade de confiança remoto não pode ser verificada ou está incorreta, o remetente deve garantir que nenhum dado foi divulgado que poderiam comprometer em si, o aplicativo ou o usuário.

Atenuantes incluem o seguinte:

- Referências de serviço devem para ser confiável. Tome cuidado sempre que a transferência de instâncias de referência de serviço para garantir que eles não foram violados.

- Alguns aplicativos podem apresentar uma experiência de usuário que permite o estabelecimento interativo de confiança com base nos dados em que os dados de referência e a confiança do serviço comprovados pelo host remoto. O WCF fornece pontos de extensibilidade para um recurso, mas o usuário deve ser implementado-los.

## <a name="ntlm"></a>NTLM

Por padrão, no ambiente de domínio do Windows, autenticação do Windows usa o protocolo Kerberos para autenticar e autorizar usuários. Se o protocolo Kerberos não pode ser usado por algum motivo, NT LAN Manager (NTLM) será usado como um fallback. Você pode desativar esse comportamento, definindo a <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> propriedade para `false`. Questões a serem consideradas ao permitir que o NTLM incluem:

- NTLM expõe o nome de usuário do cliente. Se o nome de usuário precisa ser mantidas confidenciais, em seguida, defina as `AllowNTLM` propriedade na associação à `false`.

- NTLM não oferece autenticação de servidor. Portanto, o cliente não pode garantir que ele está se comunicando com o serviço correto ao usar o NTLM como um protocolo de autenticação.

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Uso do NTLM especificando as credenciais do cliente ou de força de identidade inválido

Ao criar um cliente, especificando as credenciais do cliente sem um nome de domínio, ou especificar uma identidade de servidor inválido, faz com que o NTLM a ser usado em vez do protocolo Kerberos (se o `AllowNtlm` estiver definida como `true`). Porque o NTLM não faz a autenticação do servidor, informações potencialmente podem ser divulgadas.

Por exemplo, é possível especificar as credenciais do cliente Windows sem um nome de domínio, conforme mostrado no código a seguir em Visual C#.

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

O código não especifica um nome de domínio e, portanto NTLM será usada.

Se o domínio for especificado, mas um nome de entidade de serviço inválido é especificado usando o recurso de identidade do ponto de extremidade, o NTLM é usado. Para obter mais informações sobre como a identidade do ponto de extremidade é especificada, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).

## <a name="see-also"></a>Consulte também

- [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Ataques de reprodução](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
