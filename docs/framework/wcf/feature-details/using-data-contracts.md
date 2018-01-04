---
title: Usando contratos de dados
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
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7541f04279bbe9d85b7e2ecca841d9f5a14fc9a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-data-contracts"></a>Usando contratos de dados
Um *contrato de dados* é um contrato formal entre um serviço e um cliente que abstrata descreve os dados sejam trocados. Ou seja, para se comunicar, o cliente e o serviço não precisa compartilham os mesmos tipos, apenas os mesmos contratos de dados. Um contrato de dados define precisamente, para cada tipo de parâmetro ou retornado, quais dados são serializáveis (transformado em XML) sejam trocados.  
  
## <a name="data-contract-basics"></a>Noções básicas de contrato de dados  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usa um mecanismo de serialização chamado serializador de contrato de dados por padrão para serializar e desserializar dados (converter em XML). Todos os [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos primitivos, como números inteiros e cadeias de caracteres, bem como determinados tipos tratados como primitivos, como <xref:System.DateTime> e <xref:System.Xml.XmlElement>, pode ser serializado sem nenhuma outra preparação e são considerados como tendo contratos de dados padrão. Muitos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos também têm contratos de dados existente. Para obter uma lista completa de tipos serializáveis, consulte [tipos suportados pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Novos tipos complexos que você criar devem ter um contrato de dados definido para que eles possam ser serializáveis. Por padrão, o <xref:System.Runtime.Serialization.DataContractSerializer> infere o contrato de dados e serializa todos os tipos de publicamente visíveis. Todas as propriedades públicas de leitura/gravação e os campos do tipo são serializados. Você pode recusar membros de serialização usando o <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Você pode criar explicitamente um contrato de dados usando <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos. Normalmente, isso é feito aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> para o tipo de atributo. Esse atributo pode ser aplicado a classes, estruturas e enumerações. O <xref:System.Runtime.Serialization.DataMemberAttribute> atributo, em seguida, deve ser aplicado a cada membro do tipo de contrato de dados para indicar que ele é um *membro de dados*, ou seja, ele deve ser serializado. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um contrato de serviço (uma interface) para o qual o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos foram aplicados explicitamente. O exemplo mostra que os tipos primitivos não requerem um contrato de dados, enquanto um tipo complexo.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 O exemplo a seguir mostra como um contrato de dados para o `MyTypes.PurchaseOrder` tipo é criado aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para a classe e seus membros.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Observações  
 As observações a seguir fornecem os itens a serem considerados durante a criação de contratos de dados:  
  
-   O <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atributo será considerado somente quando usado com tipos desmarcados. Isso inclui tipos que não são marcados com um do <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, ou <xref:System.Runtime.Serialization.EnumMemberAttribute> atributos ou marcado como serializável por qualquer outro meio (como <xref:System.Xml.Serialization.IXmlSerializable>).  
  
-   Você pode aplicar o <xref:System.Runtime.Serialization.DataMemberAttribute> a campos e propriedades de atributo.  
  
-   Níveis de acessibilidade de membro (internos, privados, protegidos ou públicos) não afeta o contrato de dados de qualquer forma.  
  
-   O <xref:System.Runtime.Serialization.DataMemberAttribute> atributo será ignorado se ele é aplicado aos membros estáticos.  
  
-   Durante a serialização, código de propriedade get é chamado para membros de dados de propriedade obter o valor das propriedades a serem serializados.  
  
-   Durante a desserialização, primeiro é criado um objeto não inicializado, sem chamar nenhum construtor no tipo. Todos os membros de dados são desserializados.  
  
-   Durante a desserialização, o código do conjunto de propriedades é chamado para membros de dados de propriedade definir as propriedades para o valor que está sendo desserializado.  
  
-   Para um contrato de dados seja válido, ele deve ser possível serializar a todos os membros de dados. Para obter uma lista completa de tipos serializáveis, consulte [tipos suportados pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Tipos genéricos são tratados da mesma maneira como os tipos não genérico. Não há nenhum requisito especial para parâmetros genéricos. Por exemplo, considere o seguinte tipo.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Esse tipo pode ser serializado se o tipo usado para o parâmetro de tipo genérico (`T`) pode ser serializado ou não. Porque ele deve ser possível serializar a todos os membros de dados, o seguinte tipo é serializável somente se o parâmetro de tipo genérico também é serializável, conforme mostrado no código a seguir.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Para obter um exemplo de código completo de um serviço WCF que define um contrato de dados, consulte o [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md) exemplo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Contratos de dados compatíveis com encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Valores de padrão de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)  
 [Tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [Como criar um contrato de dados básicos para uma classe ou estrutura](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
