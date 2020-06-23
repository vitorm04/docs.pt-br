---
title: Ordem de membro de dados
description: Saiba mais sobre a ordem dos membros de dados no WCF. Os aplicativos podem precisar saber ou alterar a ordem na qual os membros de dados são enviados ou esperados.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 5c192d3bda65a7364345df4310dccd96cbe04056
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247358"
---
# <a name="data-member-order"></a><span data-ttu-id="84418-104">Ordem de membro de dados</span><span class="sxs-lookup"><span data-stu-id="84418-104">Data Member Order</span></span>
<span data-ttu-id="84418-105">Em alguns aplicativos, é útil saber a ordem na qual os dados dos vários membros de dados são enviados ou devem ser recebidos (como a ordem na qual os dados aparecem no XML serializado).</span><span class="sxs-lookup"><span data-stu-id="84418-105">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="84418-106">Às vezes, pode ser necessário alterar essa ordem.</span><span class="sxs-lookup"><span data-stu-id="84418-106">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="84418-107">Este tópico explica as regras de ordenação.</span><span class="sxs-lookup"><span data-stu-id="84418-107">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="84418-108">Regras básicas</span><span class="sxs-lookup"><span data-stu-id="84418-108">Basic Rules</span></span>  
 <span data-ttu-id="84418-109">As regras básicas para a ordenação de dados incluem:</span><span class="sxs-lookup"><span data-stu-id="84418-109">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="84418-110">Se um tipo de contrato de dados for uma parte de uma hierarquia de herança, os membros de dados de seus tipos base serão sempre primeiro na ordem.</span><span class="sxs-lookup"><span data-stu-id="84418-110">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="84418-111">A seguir, na ordem, estão os membros de dados do tipo atual que não têm a <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> Propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto de atributos, em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="84418-111">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="84418-112">A seguir estão todos os membros de dados que têm a <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> Propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="84418-112">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="84418-113">Eles são ordenados primeiro pelo valor da `Order` propriedade e, em seguida, em ordem alfabética, se houver mais de um membro de um determinado `Order` valor.</span><span class="sxs-lookup"><span data-stu-id="84418-113">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="84418-114">Os valores de ordem podem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="84418-114">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="84418-115">A ordem alfabética é estabelecida chamando o <xref:System.String.CompareOrdinal%2A> método.</span><span class="sxs-lookup"><span data-stu-id="84418-115">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="84418-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="84418-116">Examples</span></span>  
 <span data-ttu-id="84418-117">Considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="84418-117">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="84418-118">O XML produzido é semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="84418-118">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="84418-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="84418-119">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="84418-120">Equivalência de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="84418-120">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="84418-121">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="84418-121">Using Data Contracts</span></span>](using-data-contracts.md)
