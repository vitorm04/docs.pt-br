---
title: Decodificador de mensagens
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: cdfa83b722492a8b2a7b118ff70134916ed824fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="message-encoding"></a>Decodificador de mensagens
Codificação é o processo de transformar um conjunto de caracteres Unicode em uma sequência de bytes. Decodificação de é o processo inverso. Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: texto, binária e mecanismo de otimização de transmissão mensagem (MTOM).  
  
 O `binaryMessageEncoding` seção de configuração especifica o caractere de codificação e a mensagem de controle de versão usado para mensagens XML baseadas em binário. O codificador de mensagem binária codifica mensagens do Windows Communication Foundation (WCF) em binário no fio. Embora essa codificação resulta em muito rápido transmissão de mensagens, interoperabilidade com base em WS-* padrões serão perdidos.  
  
 O `mtomMessageEncoding` seção de configuração especifica o caractere de codificação e a mensagem de controle de versão usada para uma mensagem usando uma codificação de mecanismo de otimização de transmissão da mensagem (MTOM). (MTOM) é uma tecnologia eficiente para transmitir dados binários em mensagens do Windows Communication Foundation (WCF). O codificador MTOM tenta obter um equilíbrio entre eficiência e interoperabilidade. A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza o transmiti-los como blocos grandes de dados binários-é, sem conversão de texto.  
  
 O `textMessageEncoding` seção de configuração especifica um codificador de texto usado para criar mensagens de baseado em texto na conexão. Produzido por esse codificador de mensagens são adequadas para WS-* com base em interoperabilidade. Serviço Web ou cliente de serviço Web geralmente pode entender XML textual. No entanto, a transmissão de grandes blocos de dados binários como texto é o método menos eficiente para codificação de mensagens XML  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Escolhendo um codificador de mensagem](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
