---
title: Ordem de membro de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: d717673139ba810c1593e5c60e488537426f1f64
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754415"
---
# <a name="data-member-order"></a><span data-ttu-id="c32bb-102">Ordem de membro de dados</span><span class="sxs-lookup"><span data-stu-id="c32bb-102">Data Member Order</span></span>
<span data-ttu-id="c32bb-103">Em alguns aplicativos, é útil saber a ordem na qual os dados de vários membros de dados são enviados ou são esperados para ser recebida (como a ordem na qual os dados aparecem no XML serializável).</span><span class="sxs-lookup"><span data-stu-id="c32bb-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="c32bb-104">Às vezes, pode ser necessário alterar essa ordem.</span><span class="sxs-lookup"><span data-stu-id="c32bb-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="c32bb-105">Este tópico explica as regras de ordenação.</span><span class="sxs-lookup"><span data-stu-id="c32bb-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="c32bb-106">Regras básicas</span><span class="sxs-lookup"><span data-stu-id="c32bb-106">Basic Rules</span></span>  
 <span data-ttu-id="c32bb-107">As regras básicas de ordenação de dados incluem:</span><span class="sxs-lookup"><span data-stu-id="c32bb-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="c32bb-108">Se um tipo de contrato de dados fizer parte de uma hierarquia de herança, membros de dados de seus tipos base são sempre primeiros na ordem.</span><span class="sxs-lookup"><span data-stu-id="c32bb-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="c32bb-109">Em seguida, em ordem são membros de dados do tipo atual que não têm o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto em ordem alfabética de atributos.</span><span class="sxs-lookup"><span data-stu-id="c32bb-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="c32bb-110">Em seguida, estão os membros de dados que têm o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="c32bb-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="c32bb-111">Esses são ordenados pelo valor da `Order` propriedade primeiro e, em seguida, em ordem alfabética se não houver mais de um membro de um determinado `Order` valor.</span><span class="sxs-lookup"><span data-stu-id="c32bb-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="c32bb-112">Valores da ordem podem ser ignoradas.</span><span class="sxs-lookup"><span data-stu-id="c32bb-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="c32bb-113">Ordem alfabética é estabelecida chamando o <xref:System.String.CompareOrdinal%2A> método.</span><span class="sxs-lookup"><span data-stu-id="c32bb-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c32bb-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c32bb-114">Examples</span></span>  
 <span data-ttu-id="c32bb-115">Considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c32bb-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="c32bb-116">O XML gerado é semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="c32bb-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c32bb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c32bb-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="c32bb-118">Equivalência de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="c32bb-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="c32bb-119">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="c32bb-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
