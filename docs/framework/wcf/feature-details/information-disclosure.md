---
title: "Divulgação de informações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bf20f11e7077c981e73aa087c654b9cf0c87bcb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="information-disclosure"></a>Divulgação de informações
Divulgação de informações permite que um invasor obtenha informações valiosas sobre um sistema. Portanto, sempre considere quais informações são revelar e se ele pode ser usado por um usuário mal-intencionado. A seguir lista os ataques de divulgação de informações possíveis e fornece atenuantes para cada.  
  
## <a name="message-security-and-http"></a>HTTP e segurança de mensagem  
 Se você estiver usando segurança em nível de mensagem em uma camada de transporte HTTP, lembre-se de que a segurança em nível de mensagem não protege cabeçalhos HTTP. É a única maneira de proteger os cabeçalhos HTTP usar o transporte HTTPS em vez de HTTP. Transporte HTTPS faz com que a mensagem inteira, inclusive os cabeçalhos HTTP, sejam criptografados usando o protocolo Secure Sockets Layer (SSL).  
  
## <a name="policy-information"></a>Informações de política  
 Manter a política de segurança é importante, especialmente em cenários de Federação em que os requisitos de token emitido confidenciais ou informações de emissor de token são expostas na política. Nesses casos, a recomendação é proteger o ponto de extremidade de serviço federado diretiva para impedir que invasores obter informações sobre o serviço, como o tipo de declaração para colocar no token emitido, ou redirecionando os clientes para emissores de token mal-intencionado. Por exemplo, um invasor pode descobrir pares de nome e senha de usuário reconfigurando a cadeia de confiança federada para terminar em um emissor que executou um ataque man-in-the-middle. Também é recomendável que verifique se clientes federados que obtêm suas associações a recuperação de política que confiam os emissores na cadeia de confiança federada obtido. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]cenários de federação, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md).  
  
## <a name="memory-dumps-can-reveal-claim-information"></a>Despejos de memória podem revelar informações de declaração  
 Quando um aplicativo falhar, arquivos de log, como aqueles produzidos pela recuperação de desastres. Watson, pode conter as informações de declaração. Essas informações não devem ser exportadas para outras entidades, como as equipes de suporte; Caso contrário, as informações de declaração que contém dados privados também serão exportadas. Você pode mitigar isso enviando não os arquivos de log para entidades desconhecidas. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Do Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=89160).  
  
## <a name="endpoint-addresses"></a>Endereços do ponto de extremidade  
 Um endereço de ponto de extremidade contém as informações necessárias para se comunicar com um ponto de extremidade. Segurança SOAP deve incluir o endereço completo em que as mensagens de negociação de segurança que são trocadas para negociar uma chave simétrica entre um cliente e um servidor. Porque a negociação de segurança é um processo de inicialização, os cabeçalhos de endereço não podem ser criptografados durante esse processo. Portanto, o endereço não deve conter dados confidenciais; Caso contrário, isso leva a ataques de divulgação de informações.  
  
## <a name="certificates-transferred-unencrypted"></a>Certificados transferidos não criptografado  
 Quando você usa um certificado x. 509 para autenticar um cliente, o certificado é transferido de modo transparente, dentro do cabeçalho SOAP. Esteja atento isso como uma potencial divulgação de informações de identificação pessoal (PII). Isso não é um problema para `TransportWithMessageCredential` modo, onde a mensagem inteira é criptografada com segurança em nível de transporte.  
  
## <a name="service-references"></a>Referências de serviço  
 Uma referência de serviço é uma referência a outro serviço. Por exemplo, um serviço pode passar uma referência de serviço para um cliente no decorrer de uma operação. A referência de serviço também é usada com um *Verificador de identidade de confiança*, um componente interno que garante a identidade da entidade de destino antes de divulgação de informações como dados de aplicativo ou as credenciais para o destino. Se a identidade de confiança remoto não pode ser verificada ou está incorreta, o remetente deve garantir que nenhum dado foi divulgado que pode comprometer a mesmo, o aplicativo ou o usuário.  
  
 Atenuantes incluem o seguinte:  
  
-   Referências de serviço devem para ser confiável. Lembre-se sempre que a transferência de instâncias de referência de serviço para garantir que eles não foram violados.  
  
-   Alguns aplicativos podem apresentar uma experiência de usuário que permite interativo estabelecimento de confiança com base nos dados os dados de referência e a confiança do serviço comprovados pelo host remoto. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece a extensibilidade pontos para um recurso, mas o usuário devem implementados.  
  
## <a name="ntlm"></a>NTLM  
 Por padrão, no ambiente de domínio do Windows, autenticação do Windows usa o protocolo Kerberos para autenticar e autorizar usuários. Se o protocolo Kerberos não pode ser usado por algum motivo, NT LAN Manager (NTLM) será usado como um fallback. Você pode desativar esse comportamento, definindo a <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> propriedade `false`. Questões a serem consideradas ao permitir que o NTLM incluem:  
  
-   NTLM expõe o nome de usuário do cliente. Se o nome de usuário precisa ser mantidos confidenciais, em seguida, defina o `AllowNTLM` propriedade em associação com `false`.  
  
-   NTLM não fornece autenticação de servidor. Portanto, o cliente não pode garantir que ele está se comunicando com o serviço correto ao usar o NTLM como um protocolo de autenticação.  
  
### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Especificar as credenciais do cliente ou identidade inválida força uso do NTLM  
 Ao criar um cliente, especificando as credenciais do cliente sem um nome de domínio ou especificar uma identidade inválida do servidor, faz com que o NTLM ser usado em vez do protocolo Kerberos (se o `AlllowNtlm` está definida como `true`). Porque o NTLM não fazer a autenticação do servidor, informações potencialmente podem ser divulgadas.  
  
 Por exemplo, é possível especificar as credenciais do cliente Windows sem um nome de domínio, conforme mostrado no seguinte [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] código.  
  
```  
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");  
```  
  
 O código não especificar um nome de domínio e, portanto, o NTLM será usado.  
  
 Se o domínio for especificado, mas um nome de entidade de serviço inválido é especificado usando o recurso de identidade do ponto de extremidade, o NTLM é usado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como a identidade do ponto de extremidade for especificada, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Elevação de privilégio](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Negação de serviço](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Violação](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Cenários sem suporte](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Ataques de repetição](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
