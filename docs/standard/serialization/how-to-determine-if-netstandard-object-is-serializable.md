---
title: "Como: determinar se um objeto .NET padrão é serializável"
description: "Mostra como determinar se um tipo .NET padrão pode ser serializado em tempo de execução."
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c44e350ad4e561f03bf6c598172058a0a9ca41e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="a3e18-103">Como: determinar se um objeto .NET padrão é serializável</span><span class="sxs-lookup"><span data-stu-id="a3e18-103">How to: Determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="a3e18-104">O padrão do .NET é uma especificação que define os tipos e membros que devem estar presentes em implementações específicas do .NET que estão em conformidade com essa versão do padrão.</span><span class="sxs-lookup"><span data-stu-id="a3e18-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="a3e18-105">No entanto, o padrão do .NET não define se um tipo é serializável.</span><span class="sxs-lookup"><span data-stu-id="a3e18-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="a3e18-106">Os tipos definidos na biblioteca .NET padrão não são marcados com o <xref:System.SerializableAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="a3e18-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="a3e18-107">Em vez disso, implementações específicas do .NET, como o .NET Framework e o .NET Core serão livres para determinar se um determinado tipo é serializável.</span><span class="sxs-lookup"><span data-stu-id="a3e18-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="a3e18-108">Se você desenvolveu uma biblioteca que tem como destino padrão do .NET, a biblioteca pode ser consumida por qualquer implementação do .NET que oferece suporte ao padrão do .NET.</span><span class="sxs-lookup"><span data-stu-id="a3e18-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="a3e18-109">Isso significa que você não pode saber com antecedência se um tipo específico é serializável; Você somente pode determinar se é serializável em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a3e18-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="a3e18-110">Você pode determinar se um objeto é serializado em tempo de execução por recuperar o valor da <xref:System.Type.IsSerializable> propriedade de um <xref:System.Type> objeto que representa o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="a3e18-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="a3e18-111">O exemplo a seguir fornece uma implementação.</span><span class="sxs-lookup"><span data-stu-id="a3e18-111">The following example provides one implementation.</span></span> <span data-ttu-id="a3e18-112">Define uma `IsSerializable(Object)` método de extensão que indica se qualquer <xref:System.Object> instância pode ser serializada.</span><span class="sxs-lookup"><span data-stu-id="a3e18-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="a3e18-113">Você pode passar qualquer objeto para o método para determinar se ele pode ser serializado e desserializado na implementação atual do .NET, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="a3e18-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a><span data-ttu-id="a3e18-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3e18-114">See also</span></span>

<span data-ttu-id="a3e18-115">[Serialização binária](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="a3e18-115">[Binary serialization](binary-serialization.md) </span></span>  
<span data-ttu-id="a3e18-116"><xref:System.SerializableAttribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a3e18-116"><xref:System.SerializableAttribute?displayProperty=fullName></span></span>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
