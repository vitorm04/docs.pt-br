---
title: Usando contratos de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 0f33bdc006c6b965ba60257637f3cef182555d7d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637717"
---
# <a name="using-data-contracts"></a>Usando contratos de dados
Um *contrato de dados* é um contrato formal entre um serviço e um cliente que agrupa abstratamente descreve os dados a serem trocados. Ou seja, para se comunicar, o cliente e o serviço não precisa compartilhar os mesmos tipos, apenas os mesmos contratos de dados. Precisamente define um contrato de dados, para cada tipo de parâmetro ou retornado, quais dados são serializados (transformadas em XML) a ser trocado.  
  
## <a name="data-contract-basics"></a>Noções básicas de contrato de dados  
 Windows Communication Foundation (WCF) usa um mecanismo de serialização chamado o serializador de contrato de dados por padrão para serializar e desserializar dados (converter para e do XML). Todos os [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos primitivos, como inteiros e cadeias de caracteres, bem como alguns tipos tratados como primitivos, como <xref:System.DateTime> e <xref:System.Xml.XmlElement>, pode ser serializado com nenhuma outra preparação e são considerados como tendo os contratos de dados padrão. Muitos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos também têm contratos de dados existente. Para obter uma lista completa de tipos serializáveis, consulte [tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Novos tipos complexos que você criar devem ter um contrato de dados definido para que eles possam ser serializáveis. Por padrão, o <xref:System.Runtime.Serialization.DataContractSerializer> infere o contrato de dados e serializa todos os tipos visíveis publicamente. Todas as propriedades de leitura/gravação pública e campos do tipo são serializados. Você pode aceitar os membros da serialização usando o <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Você pode também criar explicitamente um contrato de dados usando <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos. Normalmente, isso é feito por meio da aplicação de <xref:System.Runtime.Serialization.DataContractAttribute> para o tipo de atributo. Esse atributo pode ser aplicado a classes, estruturas e enumerações. O <xref:System.Runtime.Serialization.DataMemberAttribute> atributo, em seguida, deve ser aplicado a cada membro do tipo de contrato de dados para indicar que ele é um *membro de dados*, ou seja, ele deve ser serializado. Para obter mais informações, consulte [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um contrato de serviço (uma interface) para o qual o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos tiverem sido aplicados explicitamente. O exemplo mostra que os tipos primitivos não exigem um contrato de dados, ao contrário de um tipo complexo.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 O exemplo a seguir mostra como um contrato de dados para o `MyTypes.PurchaseOrder` tipo é criado aplicando a <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para a classe e seus membros.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Observações  
 As observações a seguir fornecem os itens a serem considerados durante a criação de contratos de dados:  
  
- O <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atributo será considerado somente quando usado com tipos desmarcados. Isso inclui tipos que não são marcados com um dos <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, ou <xref:System.Runtime.Serialization.EnumMemberAttribute> atributos ou marcado como serializável por outros meios (como <xref:System.Xml.Serialization.IXmlSerializable>).  
  
- Você pode aplicar o <xref:System.Runtime.Serialization.DataMemberAttribute> para campos e propriedades de atributo.  
  
- Níveis de acessibilidade de membro (internos, privados, protegidos ou públicos) não afetam o contrato de dados de qualquer forma.  
  
- O <xref:System.Runtime.Serialization.DataMemberAttribute> atributo é ignorado se for aplicado a membros estáticos.  
  
- Durante a serialização, o código de propriedade get é chamado para membros de dados de propriedade obter o valor das propriedades a serem serializados.  
  
- Durante a desserialização, primeiro é criado um objeto não inicializado, sem chamar nenhum construtor no tipo. Em seguida, todos os membros de dados são desserializados.  
  
- Durante a desserialização, o código do conjunto de propriedades é chamado para membros de dados de propriedade definir as propriedades para o valor que está sendo desserializado.  
  
- Para um contrato de dados seja válido, ele deve ser possível serializar todos os seus membros de dados. Para obter uma lista completa de tipos serializáveis, consulte [tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Tipos genéricos são tratados da mesma forma como os tipos não genéricos. Não há nenhum requisito especial para parâmetros genéricos. Por exemplo, considere o seguinte tipo.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Esse tipo é serializável, se o tipo é usado para o parâmetro de tipo genérico (`T`) é serializável ou não. Como deve ser possível serializar todos os membros de dados, o seguinte tipo é serializável somente se o parâmetro de tipo genérico também é serializável, conforme mostrado no código a seguir.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Para obter um exemplo de código completo de um serviço WCF que define um contrato de dados, consulte o [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md) exemplo.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Contratos de dados compatíveis com encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [Controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [Valores de padrão de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)
- [Tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [Como: Criar um contrato de dados básicos para uma classe ou estrutura](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
