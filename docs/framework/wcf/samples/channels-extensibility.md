---
title: Extensibilidade de canais
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e0cf92edc4ec05df3e5e8c25b90bcf253e94ed6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="channels-extensibility"></a>Extensibilidade de canais
Esta seção contém exemplos que demonstram os canais personalizados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Canal local](../../../../docs/framework/wcf/samples/local-channel.md)  
 Demonstra o canal local, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] canal de transporte que é usado para comunicação dentro do mesmo domínio de aplicativo.  
  
 [Perfil seguro confiável](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 Demonstra como compor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e perfil seguro confiável (RSP).  
  
 [Distribuidor de canal personalizado](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 Demonstra como criar a pilha de canais de forma personalizada implementando <xref:System.ServiceModel.ServiceHostBase> diretamente e como criar um distribuidor de canal personalizado no ambiente de host da Web.  
  
 [Canal de agrupamento](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 Demonstra como limitar a quantidade de memória usada para armazenar em buffer grandes mensagens enviadas usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Canal de reconhecimento de HTTP](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 Demonstra um canal em camadas que altera o padrão de mensagens unidirecional.  
  
 [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 Demonstra como criar um canal de protocolo personalizado para usar cookies HTTP para o gerenciamento de sessão.  
  
 [Interceptor de mensagem personalizado](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 Demonstra como implementar um elemento de associação personalizada que cria fábricas de canais e ouvintes de canais para interceptar todas as mensagens de entrada e saídas em um ponto específico na pilha de tempo de execução.
