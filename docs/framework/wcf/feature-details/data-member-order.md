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
# <a name="data-member-order"></a><span data-ttu-id="59471-102">Ordem de membro de dados</span><span class="sxs-lookup"><span data-stu-id="59471-102">Data Member Order</span></span>
<span data-ttu-id="59471-103">Em alguns aplicativos, é útil saber a ordem em que os dados dos vários membros de dados são enviados ou são esperados para serem recebidos (como a ordem em que os dados aparecem no XML serializado).</span><span class="sxs-lookup"><span data-stu-id="59471-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="59471-104">Às vezes pode ser necessário mudar essa ordem.</span><span class="sxs-lookup"><span data-stu-id="59471-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="59471-105">Este tópico explica as regras de pedidos.</span><span class="sxs-lookup"><span data-stu-id="59471-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="59471-106">Regras básicas</span><span class="sxs-lookup"><span data-stu-id="59471-106">Basic Rules</span></span>  
 <span data-ttu-id="59471-107">As regras básicas para o pedido de dados incluem:</span><span class="sxs-lookup"><span data-stu-id="59471-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="59471-108">Se um tipo de contrato de dados faz parte de uma hierarquia de herança, os membros de dados de seus tipos de base são sempre os primeiros na ordem.</span><span class="sxs-lookup"><span data-stu-id="59471-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="59471-109">Em seguida, em ordem estão os membros de <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> dados <xref:System.Runtime.Serialization.DataMemberAttribute> do tipo atual que não têm a propriedade do conjunto de atributos, em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="59471-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="59471-110">Em seguida estão os <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> membros de <xref:System.Runtime.Serialization.DataMemberAttribute> dados que tenham a propriedade do conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="59471-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="59471-111">Estes são ordenados pelo `Order` valor da propriedade primeiro e, em seguida, `Order` alfabeticamente se há mais de um membro de um determinado valor.</span><span class="sxs-lookup"><span data-stu-id="59471-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="59471-112">Os valores da ordem podem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="59471-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="59471-113">A ordem alfabética é <xref:System.String.CompareOrdinal%2A> estabelecida chamando o método.</span><span class="sxs-lookup"><span data-stu-id="59471-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="59471-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="59471-114">Examples</span></span>  
 <span data-ttu-id="59471-115">Considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="59471-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="59471-116">O XML produzido é semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="59471-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59471-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="59471-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="59471-118">Equivalência de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="59471-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="59471-119">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="59471-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
