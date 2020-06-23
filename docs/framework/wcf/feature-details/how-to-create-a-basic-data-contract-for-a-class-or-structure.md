---
title: Como criar um contrato de dados básicos para uma classe ou estrutura
description: Siga este exemplo para aprender a criar um contrato de dados usando uma classe ou estrutura no WCF usando o atributo DataContractAttribute.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: a45fde58795947c3e46fa45750ae1a3faddd8849
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247163"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="e9e82-103">Como criar um contrato de dados básicos para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="e9e82-103">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="e9e82-104">Este tópico mostra as etapas básicas para criar um contrato de dados usando uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e9e82-104">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="e9e82-105">Para obter mais informações sobre contratos de dados e como eles são usados, consulte [usando contratos de dados](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e9e82-105">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="e9e82-106">Para obter um tutorial que percorre as etapas de criação de um serviço e cliente do Windows Communication Foundation básico (WCF), consulte o [tutorial de introdução](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="e9e82-106">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="e9e82-107">Para um aplicativo de exemplo funcional que consiste em um serviço e cliente básicos, consulte [contrato de dados básico](../samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e9e82-107">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="e9e82-108">Para criar um contrato de dados básico para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="e9e82-108">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="e9e82-109">Declare que o tipo tem um contrato de dados aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> atributo à classe.</span><span class="sxs-lookup"><span data-stu-id="e9e82-109">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="e9e82-110">Observe que todos os tipos públicos, incluindo aqueles sem atributos, são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="e9e82-110">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="e9e82-111">O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados se o <xref:System.Runtime.Serialization.DataContractAttribute> atributo estiver ausente.</span><span class="sxs-lookup"><span data-stu-id="e9e82-111">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="e9e82-112">Para obter mais informações, consulte [tipos serializáveis](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="e9e82-112">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="e9e82-113">Defina os membros (Propriedades, campos ou eventos) que são serializados aplicando o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a cada membro.</span><span class="sxs-lookup"><span data-stu-id="e9e82-113">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="e9e82-114">Esses membros são chamados de membros de dados.</span><span class="sxs-lookup"><span data-stu-id="e9e82-114">These members are called data members.</span></span> <span data-ttu-id="e9e82-115">Por padrão, todos os tipos públicos são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="e9e82-115">By default, all public types are serializable.</span></span> <span data-ttu-id="e9e82-116">Para obter mais informações, consulte [tipos serializáveis](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="e9e82-116">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e9e82-117">Você pode aplicar o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a campos privados, fazendo com que os dados sejam expostos a outros.</span><span class="sxs-lookup"><span data-stu-id="e9e82-117">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="e9e82-118">Certifique-se de que o membro não contém dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="e9e82-118">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9e82-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9e82-119">Example</span></span>  
 <span data-ttu-id="e9e82-120">O exemplo a seguir mostra como criar um contrato de dados para o `Person` tipo aplicando <xref:System.Runtime.Serialization.DataContractAttribute> os <xref:System.Runtime.Serialization.DataMemberAttribute> atributos e à classe e seus membros.</span><span class="sxs-lookup"><span data-stu-id="e9e82-120">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e9e82-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="e9e82-121">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="e9e82-122">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="e9e82-122">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="e9e82-123">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="e9e82-123">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="e9e82-124">Introdução</span><span class="sxs-lookup"><span data-stu-id="e9e82-124">Getting Started</span></span>](../samples/getting-started-sample.md)
