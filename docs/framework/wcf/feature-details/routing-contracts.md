---
title: Contratos de roteamento
ms.date: 03/30/2017
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
ms.openlocfilehash: 73d303c95a636f5e90f256272726c08c581d6fdf
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396969"
---
# <a name="routing-contracts"></a>Contratos de roteamento
Contratos de roteamento definem os padrões de mensagem que o serviço de roteamento pode processar.  Cada contrato é sem especificação de tipo e permite que o serviço receber uma mensagem sem o conhecimento do esquema de mensagem ou ação. Isso permite que o serviço de roteamento genericamente rotear mensagens sem configuração adicional para as especificações das mensagens subjacentes que está sendo roteado.  
  
## <a name="routing-contracts"></a>Contratos de roteamento  
 Como o serviço de roteamento aceita um objeto Message do WCF genérico, o aspecto mais importante, ao selecionar um contrato é a forma de canal que será usado ao se comunicar com clientes e serviços. Durante o processamento de mensagens, o serviço de roteamento usa propulsores de mensagens simétricos, geralmente que a forma do contrato de entrada deve corresponder a forma do contrato de saída. No entanto, há casos onde o dispatcher do modelo de serviço pode modificar as formas, como quando o dispatcher converte um canal duplex em um canal de solicitação-resposta ou remove o suporte de sessão quando ele não é necessário e não está sendo usado (ou seja um canal Quando **SessionMode**, convertendo um **IInputSessionChannel** em um **IInputChannel**).  
  
 Para dar suporte a esses aumentos de mensagem, o serviço Routing fornece contratos no <xref:System.ServiceModel.Routing> namespace, que deve ser usado ao definir os pontos de extremidade de serviço usados pelo serviço de roteamento. Esses contratos são sem especificação de tipo, que permite que o recebimento de qualquer tipo de mensagem ou uma ação e permite que o serviço de roteamento lidar com mensagens sem o conhecimento do esquema de mensagem específica. Para obter mais informações sobre os contratos usados pelo serviço de roteamento, consulte [contratos de roteamento](../../../../docs/framework/wcf/feature-details/routing-contracts.md).  
  
 Os contratos fornecidos pelo serviço de roteamento estão localizados no <xref:System.ServiceModel.Routing> namespace e são descritos na tabela a seguir.  
  
|Contrato|Forma|Forma de canal|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel -> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode. Required<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel -> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode<br /><br /> AsyncPattern = true|IReplyChannel -> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel -> IDuplexSessionChannel|  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de roteamento](https://msdn.microsoft.com/library/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)  
 [Introdução ao roteamento](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
