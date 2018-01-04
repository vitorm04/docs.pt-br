---
title: "Como criar um contrato de dados básicos para uma classe ou estrutura"
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
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6241df0fd5a0b6ee532691eee2279f618be25a56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="e6fea-102">Como criar um contrato de dados básicos para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="e6fea-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="e6fea-103">Este tópico mostra as etapas básicas para criar um contrato de dados usando uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e6fea-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e6fea-104">contratos de dados e como eles são usados, consulte [usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e6fea-104"> data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="e6fea-105">Para obter um tutorial que percorra as etapas de criação de um basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço e cliente, consulte o [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="e6fea-105">For a tutorial that walks through the steps of creating a basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="e6fea-106">Para um aplicativo de exemplo de trabalho que consiste em um serviço básico e o cliente, consulte [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e6fea-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="e6fea-107">Para criar um contrato de dados básicos para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="e6fea-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="e6fea-108">Declare o tipo tem um contrato de dados, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> para a classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="e6fea-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="e6fea-109">Observe que todos os tipos públicos, incluindo aqueles sem atributos, são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="e6fea-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="e6fea-110">O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados se o <xref:System.Runtime.Serialization.DataContractAttribute> atributo está ausente.</span><span class="sxs-lookup"><span data-stu-id="e6fea-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e6fea-111">[Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="e6fea-111"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="e6fea-112">Definir os membros (propriedades, campos ou eventos) que são serializados aplicando o <xref:System.Runtime.Serialization.DataMemberAttribute> a cada membro de atributo.</span><span class="sxs-lookup"><span data-stu-id="e6fea-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="e6fea-113">Esses membros são chamados de membros de dados.</span><span class="sxs-lookup"><span data-stu-id="e6fea-113">These members are called data members.</span></span> <span data-ttu-id="e6fea-114">Por padrão, todos os tipos públicos são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="e6fea-114">By default, all public types are serializable.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="e6fea-115">[Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="e6fea-115"> [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e6fea-116">Você pode aplicar o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo campos particulares, fazendo com que os dados sejam expostos a outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="e6fea-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="e6fea-117">Certifique-se de que o membro não contém dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="e6fea-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6fea-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e6fea-118">Example</span></span>  
 <span data-ttu-id="e6fea-119">O exemplo a seguir mostra como criar um contrato de dados para o `Person` tipo aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para a classe e seus membros.</span><span class="sxs-lookup"><span data-stu-id="e6fea-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e6fea-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6fea-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="e6fea-121">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="e6fea-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="e6fea-122">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="e6fea-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="e6fea-123">Introdução</span><span class="sxs-lookup"><span data-stu-id="e6fea-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
