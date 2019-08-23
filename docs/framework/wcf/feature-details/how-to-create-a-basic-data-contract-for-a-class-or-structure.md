---
title: 'Como: criar um contrato de dados básicos para uma classe ou estrutura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968455"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="a0bcf-102">Como: criar um contrato de dados básicos para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="a0bcf-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="a0bcf-103">Este tópico mostra as etapas básicas para criar um contrato de dados usando uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="a0bcf-104">Para obter mais informações sobre contratos de dados e como eles são usados, consulte [usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a0bcf-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="a0bcf-105">Para obter um tutorial que percorre as etapas de criação de um serviço e cliente do Windows Communication Foundation básico (WCF), consulte o [tutorial de introdução](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a0bcf-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="a0bcf-106">Para um aplicativo de exemplo funcional que consiste em um serviço e cliente básicos, consulte [contrato de dados básico](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="a0bcf-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="a0bcf-107">Para criar um contrato de dados básico para uma classe ou estrutura</span><span class="sxs-lookup"><span data-stu-id="a0bcf-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="a0bcf-108">Declare que o tipo tem um contrato de dados aplicando <xref:System.Runtime.Serialization.DataContractAttribute> o atributo à classe.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="a0bcf-109">Observe que todos os tipos públicos, incluindo aqueles sem atributos, são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="a0bcf-110">O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados se <xref:System.Runtime.Serialization.DataContractAttribute> o atributo estiver ausente.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="a0bcf-111">Para obter mais informações, consulte [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="a0bcf-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2. <span data-ttu-id="a0bcf-112">Defina os membros (Propriedades, campos ou eventos) que são serializados aplicando o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a cada membro.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="a0bcf-113">Esses membros são chamados de membros de dados.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-113">These members are called data members.</span></span> <span data-ttu-id="a0bcf-114">Por padrão, todos os tipos públicos são serializáveis.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-114">By default, all public types are serializable.</span></span> <span data-ttu-id="a0bcf-115">Para obter mais informações, consulte [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="a0bcf-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a0bcf-116">Você pode aplicar o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo a campos privados, fazendo com que os dados sejam expostos a outros.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="a0bcf-117">Certifique-se de que o membro não contém dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0bcf-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0bcf-118">Example</span></span>  
 <span data-ttu-id="a0bcf-119">O exemplo a seguir mostra como criar um contrato de dados para `Person` o tipo aplicando <xref:System.Runtime.Serialization.DataContractAttribute> os <xref:System.Runtime.Serialization.DataMemberAttribute> atributos e à classe e seus membros.</span><span class="sxs-lookup"><span data-stu-id="a0bcf-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a0bcf-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0bcf-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="a0bcf-121">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="a0bcf-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="a0bcf-122">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="a0bcf-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="a0bcf-123">Introdução</span><span class="sxs-lookup"><span data-stu-id="a0bcf-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
