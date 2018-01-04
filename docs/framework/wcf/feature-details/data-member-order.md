---
title: Ordem de membro de dados
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
helpviewer_keywords: data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41eb191a08aba0f84a677087a3771b6d8e90efcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-member-order"></a><span data-ttu-id="387e4-102">Ordem de membro de dados</span><span class="sxs-lookup"><span data-stu-id="387e4-102">Data Member Order</span></span>
<span data-ttu-id="387e4-103">Em alguns aplicativos, é útil saber a ordem na qual os dados de vários membros de dados são enviados ou deve ser recebida (por exemplo, a ordem em que os dados aparecem no XML serializado).</span><span class="sxs-lookup"><span data-stu-id="387e4-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="387e4-104">Às vezes, pode ser necessário alterar essa ordem.</span><span class="sxs-lookup"><span data-stu-id="387e4-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="387e4-105">Este tópico explica as regras de ordenação.</span><span class="sxs-lookup"><span data-stu-id="387e4-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="387e4-106">Regras básicas</span><span class="sxs-lookup"><span data-stu-id="387e4-106">Basic Rules</span></span>  
 <span data-ttu-id="387e4-107">As regras básicas de ordenação de dados incluem:</span><span class="sxs-lookup"><span data-stu-id="387e4-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="387e4-108">Se um tipo de contrato de dados fizer parte de uma hierarquia de herança, membros de dados de seus tipos base são sempre primeiras na ordem.</span><span class="sxs-lookup"><span data-stu-id="387e4-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="387e4-109">Em seguida em ordem são membros de dados do tipo que não têm o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto em ordem alfabética de atributos.</span><span class="sxs-lookup"><span data-stu-id="387e4-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="387e4-110">Em seguida são os membros de dados que tem o <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> conjunto de atributos.</span><span class="sxs-lookup"><span data-stu-id="387e4-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="387e4-111">Esses são ordenados pelo valor da `Order` propriedade primeiro e, em seguida, em ordem alfabética se houver mais de um membro de um determinado `Order` valor.</span><span class="sxs-lookup"><span data-stu-id="387e4-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="387e4-112">Valores da ordem podem ser ignorados.</span><span class="sxs-lookup"><span data-stu-id="387e4-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="387e4-113">Ordem alfabética é estabelecida chamando o <xref:System.String.CompareOrdinal%2A> método.</span><span class="sxs-lookup"><span data-stu-id="387e4-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="387e4-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="387e4-114">Examples</span></span>  
 <span data-ttu-id="387e4-115">Considere o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="387e4-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="387e4-116">O XML gerado é semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="387e4-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="387e4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="387e4-117">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [<span data-ttu-id="387e4-118">Equivalência de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="387e4-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [<span data-ttu-id="387e4-119">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="387e4-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
