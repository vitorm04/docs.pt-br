---
title: Retornos de chamada de serialização tolerantes à versão
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 0736f94b1fe1a91b20ee76da673e0bc139aa802a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959562"
---
# <a name="version-tolerant-serialization-callbacks"></a>Retornos de chamada de serialização tolerantes à versão
O modelo de programação de contrato de dados dá suporte total aos métodos de retorno de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> chamada <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> de serialização tolerantes à versão que as classes e dão suporte.  
  
## <a name="version-tolerant-attributes"></a>Atributos tolerantes à versão  
 Há quatro atributos de retorno de chamada. Cada atributo pode ser aplicado a um método que o mecanismo de serialização/desserialização chama em vários momentos. A tabela a seguir explica quando usar cada atributo.  
  
|Atributo|Quando o método correspondente é chamado|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Chamado antes de serializar o tipo.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Chamado após a serialização do tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Chamado antes de desserializar o tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Chamado após a desserialização do tipo.|  
  
 Os métodos devem aceitar um <xref:System.Runtime.Serialization.StreamingContext> parâmetro.  
  
 Esses métodos se destinam principalmente ao uso com controle de versão ou inicialização. Durante a desserialização, nenhum construtor é chamado. Portanto, os membros de dados podem não ser inicializados corretamente (para valores padrão pretendidos) se os dados desses membros estiverem ausentes no fluxo de entrada, por exemplo, se os dados vierem de uma versão anterior de um tipo que não tem alguns membros de dados. Para corrigir isso, use o método de retorno de chamada <xref:System.Runtime.Serialization.OnDeserializingAttribute>marcado com o, conforme mostrado no exemplo a seguir.  
  
 Você pode marcar apenas um método por tipo com cada um dos atributos de retorno de chamada anteriores.  
  
### <a name="example"></a>Exemplo  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Serialização tolerante a versão](../../../standard/serialization/version-tolerant-serialization.md)
