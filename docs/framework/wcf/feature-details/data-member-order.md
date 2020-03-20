---
title: Ordem de membro de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 2a5d7430953bdc31644e92b9207cd2865209cce5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185192"
---
# <a name="data-member-order"></a>Ordem de membro de dados
Em alguns aplicativos, é útil saber a ordem em que os dados dos vários membros de dados são enviados ou são esperados para serem recebidos (como a ordem em que os dados aparecem no XML serializado). Às vezes pode ser necessário mudar essa ordem. Este tópico explica as regras de pedidos.  
  
## <a name="basic-rules"></a>Regras básicas  
 As regras básicas para o pedido de dados incluem:  
  
- Se um tipo de contrato de dados faz parte de uma hierarquia de herança, os membros de dados de seus tipos de base são sempre os primeiros na ordem.  
  
- Em seguida, em ordem estão os membros de <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> dados <xref:System.Runtime.Serialization.DataMemberAttribute> do tipo atual que não têm a propriedade do conjunto de atributos, em ordem alfabética.  
  
- Em seguida estão os <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> membros de <xref:System.Runtime.Serialization.DataMemberAttribute> dados que tenham a propriedade do conjunto de atributos. Estes são ordenados pelo `Order` valor da propriedade primeiro e, em seguida, `Order` alfabeticamente se há mais de um membro de um determinado valor. Os valores da ordem podem ser ignorados.  
  
 A ordem alfabética é <xref:System.String.CompareOrdinal%2A> estabelecida chamando o método.  
  
## <a name="examples"></a>Exemplos  
 Considere o código a seguir.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 O XML produzido é semelhante ao seguinte.  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>
</DerivedType>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
