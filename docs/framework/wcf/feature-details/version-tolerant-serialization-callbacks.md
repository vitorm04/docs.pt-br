---
title: "Retornos de chamada de serialização tolerantes à versão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c00cadd4b0e643e35f7f56a28760e261c423699
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="version-tolerant-serialization-callbacks"></a>Retornos de chamada de serialização tolerantes à versão
O modelo de programação de contrato de dados suporta totalmente os métodos de retorno de chamada de serialização tolerantes à versão que o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes de suporte.  
  
## <a name="version-tolerant-attributes"></a>Atributos tolerantes à versão  
 Há quatro atributos de retorno de chamada. Cada atributo pode ser aplicado a um método que chama o mecanismo de serialização/desserialização várias vezes. A tabela a seguir explica quando usar cada atributo.  
  
|Atributo|Quando o método correspondente é chamado|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Chamado antes de serializar o tipo.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Chamado após a serialização do tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Chamado antes de desserializar o tipo.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Chamado após a desserialização do tipo.|  
  
 Os métodos devem aceitar um <xref:System.Runtime.Serialization.StreamingContext> parâmetro.  
  
 Esses métodos são principalmente para uso com controle de versão ou de inicialização. Durante a desserialização, não é chamados de nenhum construtor. Portanto, os membros de dados podem não ser inicializados corretamente (para valores padrão pretendido) se os dados para esses membros estão ausentes no fluxo de entrada, por exemplo, se os dados vêm de uma versão anterior de um tipo que não tem alguns membros de dados. Para corrigir isso, use o método de retorno de chamada marcado com o <xref:System.Runtime.Serialization.OnDeserializingAttribute>, conforme mostrado no exemplo a seguir.  
  
 Você pode marcar apenas um método por tipo, com cada um dos atributos precedentes de retorno de chamada.  
  
### <a name="example"></a>Exemplo  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [Serialização tolerante a versão](../../../../docs/standard/serialization/version-tolerant-serialization.md)
