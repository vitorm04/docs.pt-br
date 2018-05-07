---
title: Ordem de membro de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: e286b900d7647bcd5bc99b78164e6820c1417a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="data-member-order"></a>Ordem de membro de dados
Em alguns aplicativos, é útil saber a ordem na qual os dados de vários membros de dados são enviados ou deve ser recebida (por exemplo, a ordem em que os dados aparecem no XML serializado). Às vezes, pode ser necessário alterar essa ordem. Este tópico explica as regras de ordenação.  
  
## <a name="basic-rules"></a>Regras básicas  
 As regras básicas de ordenação de dados incluem:  
  
-   Se um tipo de contrato de dados fizer parte de uma hierarquia de herança, membros de dados de seus tipos base são sempre primeiras na ordem.  
  
-   Em seguida em ordem são membros de dados do tipo que não têm o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto em ordem alfabética de atributos.  
  
-   Em seguida são os membros de dados que tem o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto de atributos. Esses são ordenados pelo valor da `Order` propriedade primeiro e, em seguida, em ordem alfabética se houver mais de um membro de um determinado `Order` valor. Valores da ordem podem ser ignorados.  
  
 Ordem alfabética é estabelecida chamando o <xref:System.String.CompareOrdinal%2A> método.  
  
## <a name="examples"></a>Exemplos  
 Considere o código a seguir.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 O XML gerado é semelhante ao seguinte.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Equivalência de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
