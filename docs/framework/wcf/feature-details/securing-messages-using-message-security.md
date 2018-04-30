---
title: Protegendo as mensagens com a segurança de mensagens
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
caps.latest.revision: 16
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 088b01151d0471527bbfc2ffa04b5b5064700081
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="securing-messages-using-message-security"></a>Protegendo as mensagens com a segurança de mensagens
Esta seção discute [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança da mensagem ao usar <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Antes de ler este tópico, é recomendável que você leia [conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 A ilustração a seguir fornece um modelo conceitual de comunicação em fila usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Esta ilustração e terminologia são usados para explicar  
  
 conceitos de segurança de transporte.  
  
 ![Na fila de diagrama do aplicativo](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Figura distribuídas de fila")  
  
 Ao enviar mensagens em fila usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagem for anexada como um corpo da mensagem de enfileiramento de mensagens (MSMQ). Enquanto a segurança de transporte protege o inteiro MSMQ mensagem, mensagem (ou SOAP) segurança protege apenas o corpo da mensagem do MSMQ.  
  
 O conceito de chave de segurança de mensagem é que o cliente protege a mensagem para o aplicativo de recebimento (serviço), ao contrário de segurança de transporte em que o cliente protege a mensagem para a fila de destino. Como tal, MSMQ não desempenha nenhuma parte ao proteger o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagem usando a segurança de mensagem.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança de mensagem adiciona cabeçalhos de segurança para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagem que se integram infra-estruturas de segurança existentes, como um certificado ou o protocolo Kerberos.  
  
## <a name="message-credential-type"></a>Tipo de credencial de mensagem  
 Usando a segurança de mensagem, o serviço e o cliente poderá apresentar credenciais para autenticar entre si. Você pode selecionar a segurança de mensagem, definindo o <xref:System.ServiceModel.NetMsmqBinding.Security%2A> modo para `Message` ou `Both` (ou seja, use a segurança de transporte e segurança de mensagem).  
  
 O serviço pode usar o <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> propriedade para inspecionar a credencial usada para autenticar o cliente. Isso também pode ser usado para outras verificações de autorização decidir implementar o serviço.  
  
 Esta seção explica os diferentes tipos de credenciais e como usá-los com as filas.  
  
### <a name="certificate"></a>certificado  
 O tipo de credencial de certificado usa um certificado x. 509 para identificar o cliente e o serviço.  
  
 Em um cenário típico, o cliente e o serviço são emitidos um certificado válido por uma autoridade de certificação confiável. Em seguida, a conexão é estabelecida, o cliente autentica a validade do serviço usando o certificado do serviço para decidir se pode contar com o serviço. Da mesma forma, o serviço usa o certificado do cliente para validar a confiança do cliente.  
  
 Devido à natureza desconectada de filas, o cliente e o serviço podem não estar online ao mesmo tempo. Como tal, o cliente e o serviço precisam trocar certificados de fora da banda. Em particular, o cliente, em virtude mantendo o certificado do serviço (que pode ser vinculado a uma autoridade de certificação) em seu repositório confiável, deve confiar que ele está se comunicando com o serviço correto. Para autenticar o cliente, o serviço usa o certificado x. 509 anexado com uma mensagem que faz a correspondência com o certificado em seu repositório para verificar a autenticidade do cliente. Novamente, o certificado deve ser ligado a uma autoridade de certificação.  
  
 Em um computador executando o Windows, certificados são mantidos em vários tipos de armazenamentos. Para obter mais informações sobre os repositórios diferentes, consulte [repositórios de certificados](http://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Tipo de credencial de mensagem do Windows usa o protocolo Kerberos.  
  
 O protocolo Kerberos é um mecanismo de segurança que autentica os usuários em um domínio e permite que os usuários autenticados estabelecer contextos seguros com outras entidades em um domínio.  
  
 Usando o protocolo Kerberos para comunicação em fila o problema é que as permissões que contêm a identidade do cliente que distribui o Centro de distribuição de chaves (KDC) são relativamente curta duração. Um *tempo de vida* está associado com o tíquete Kerberos que indica a validade do tíquete de. Assim, considerando alta latência, você não pode ser-se de que o token ainda é válido para o serviço que autentica o cliente.  
  
 Observe que, ao usar esse tipo de credencial, o serviço deve ser executado sob a conta de serviço.  
  
 O protocolo Kerberos é usado por padrão, ao escolher a credencial da mensagem. Para obter mais informações, consulte [explorando Kerberos, o protocolo de segurança distribuído no Windows 2000](http://go.microsoft.com/fwlink/?LinkId=87790).  
  
### <a name="username-password"></a>Senha do nome de usuário  
 Usando essa propriedade, o cliente pode autenticar para o servidor usando uma senha de nome de usuário no cabeçalho de segurança da mensagem.  
  
### <a name="issuedtoken"></a>IssuedToken  
 O cliente pode usar o serviço de token de segurança para emitir um token que pode ser anexado à mensagem para o serviço autenticar o cliente.  
  
## <a name="using-transport-and-message-security"></a>Usando o transporte e segurança de mensagem  
 Ao usar a segurança de transporte e segurança de mensagem, o certificado usado para proteger a mensagem no transporte e o nível de mensagem SOAP deve ser o mesmo.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo mensagens usando a segurança do transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Segurança de mensagem através do enfileiramento de mensagem](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 [Conceitos de segurança](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
