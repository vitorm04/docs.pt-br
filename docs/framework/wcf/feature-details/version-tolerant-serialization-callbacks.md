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
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124625"
---
# <a name="version-tolerant-serialization-callbacks"></a>Retornos de chamada de serialização tolerantes à versão
O modelo de programação de contrato de dados totalmente compatível com os métodos de retorno de chamada de serialização tolerantes à versão que o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes oferecem suporte.  
  
## <a name="version-tolerant-attributes"></a>Atributos tolerantes à versão  
 Há quatro atributos de retorno de chamada. Cada atributo pode ser aplicado a um método que o mecanismo de serialização/desserialização chama em vários momentos. A tabela a seguir explica quando usar cada atributo.  
  
|Atributo|Quando o método correspondente é chamado|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Chamado antes de serializar o tipo.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Chamado depois de serializar o tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Chamado antes de desserializar o tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Chamado depois de desserializar o tipo.|  
  
 Os métodos devem aceitar uma <xref:System.Runtime.Serialization.StreamingContext> parâmetro.  
  
 Esses métodos destinam-se principalmente para uso com o controle de versão ou de inicialização. Durante a desserialização, nenhum construtor é chamado. Portanto, os membros de dados podem não ser inicializados corretamente (para valores padrão pretendido) se os dados para esses membros estão ausentes no fluxo de entrada, por exemplo, se os dados vêm de uma versão anterior de um tipo que está faltando alguns membros de dados. Para corrigir isso, use o método de retorno de chamada marcado com o <xref:System.Runtime.Serialization.OnDeserializingAttribute>, conforme mostrado no exemplo a seguir.  
  
 Você pode marcar apenas um método por tipo, com cada um dos atributos precedentes do retorno de chamada.  
  
### <a name="example"></a>Exemplo  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Serialização tolerante a versão](../../../../docs/standard/serialization/version-tolerant-serialization.md)
