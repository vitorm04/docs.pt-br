---
title: Como determinar se um objeto .NET padrão é serializável
description: Mostra como determinar se um tipo .NET Standard pode ser serializado em tempo de execução.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881402"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="c3dde-103">Como determinar se um objeto .NET padrão é serializável</span><span class="sxs-lookup"><span data-stu-id="c3dde-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="c3dde-104">O .NET Standard é uma especificação que define os tipos e membros que devem estar presentes em implementações específicas do .NET que estão em conformidade com essa versão do padrão.</span><span class="sxs-lookup"><span data-stu-id="c3dde-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="c3dde-105">No entanto, o .NET Standard não define se um tipo é serializável.</span><span class="sxs-lookup"><span data-stu-id="c3dde-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="c3dde-106">Os tipos definidos na biblioteca do .NET Standard não são marcados com o <xref:System.SerializableAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="c3dde-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="c3dde-107">Em vez disso, a implementações específicas do .NET, como o .NET Framework e .NET Core, são livres para determinar se um determinado tipo é serializável.</span><span class="sxs-lookup"><span data-stu-id="c3dde-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="c3dde-108">Se você tiver desenvolvido uma biblioteca que tem como alvo o .NET Standard, sua biblioteca pode ser consumida por qualquer implementação do .NET que dá suporte a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c3dde-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="c3dde-109">Isso significa que você não pode saber de antemão se um determinado tipo é serializável; Você somente pode determinar se ele é serializável em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c3dde-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="c3dde-110">Você pode determinar se um objeto é serializável em tempo de execução ao recuperar o valor da <xref:System.Type.IsSerializable> propriedade de um <xref:System.Type> objeto que representa o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="c3dde-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="c3dde-111">O exemplo a seguir fornece uma implementação.</span><span class="sxs-lookup"><span data-stu-id="c3dde-111">The following example provides one implementation.</span></span> <span data-ttu-id="c3dde-112">Ele define uma `IsSerializable(Object)` método de extensão que indica se qualquer <xref:System.Object> instância pode ser serializada.</span><span class="sxs-lookup"><span data-stu-id="c3dde-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="c3dde-113">Em seguida, você pode passar qualquer objeto para o método para determinar se ele pode ser serializado e desserializado na implementação atual do .NET, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c3dde-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="c3dde-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3dde-114">See also</span></span>

- [<span data-ttu-id="c3dde-115">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="c3dde-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
