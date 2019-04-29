---
title: Decodificador de mensagens
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: 7fb0d4a994eaf1497841691eb76261329a48599d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768986"
---
# <a name="message-encoding"></a>Decodificador de mensagens
Codificação é o processo de transformar um conjunto de caracteres Unicode em uma sequência de bytes. Decodificação de é o processo inverso. Windows Communication Foundation (WCF) inclui três tipos de codificação para mensagens SOAP: Texto, binária e mecanismo de otimização de transmissão de mensagens (MTOM).  
  
 O `binaryMessageEncoding` seção de configuração especifica o caractere de codificação e a mensagem de controle de versão usado para mensagens XML baseadas em binário. O codificador de mensagem binária codifica mensagens do Windows Communication Foundation (WCF) em binário no fio. Embora essa codificação resulta em muito rápido transmissão de mensagens, interoperabilidade com base no WS-* padrões é perdido.  
  
 O `mtomMessageEncoding` seção de configuração especifica o caractere de codificação e a mensagem de controle de versão usado para uma mensagem usando a codificação de MTOM Message Transmission Optimization Mechanism (). (MTOM) é uma tecnologia eficiente para a transmissão de dados binários nas mensagens do Windows Communication Foundation (WCF). O codificador MTOM tenta obter um equilíbrio entre a eficiência e interoperabilidade. A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza blocos grandes de dados binários, transmiti-los como-está, sem a conversão em texto.  
  
 O `textMessageEncoding` seção de configuração especifica um codificador de texto usado para criar mensagens baseadas em texto durante a transmissão. As mensagens geradas por esse codificador são adequadas para WS-* com base em interoperabilidade. Serviço Web ou o cliente do serviço Web geralmente pode compreender XML textual. No entanto, a transmissão de blocos grandes de dados binários como texto é o método menos eficiente para codificação de mensagens XML  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Escolhendo um codificador de mensagem](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
