---
title: Como determinar se um objeto de .NET Standard é serializável
description: Mostra como determinar se um tipo de .NET Standard pode ser serializado em tempo de execução.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: 9f7ab8a824b9687f68382a5edc342536289c5d09
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282319"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="7ceb9-103">Como determinar se um objeto de .NET Standard é serializável</span><span class="sxs-lookup"><span data-stu-id="7ceb9-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="7ceb9-104">.NET Standard é uma especificação que define os tipos e membros que devem estar presentes em implementações específicas do .NET que estão em conformidade com essa versão do padrão.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-104">.NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="7ceb9-105">No entanto, .NET Standard não define se um tipo é serializável.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-105">However, .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="7ceb9-106">Os tipos definidos na biblioteca de .NET Standard não são marcados com o <xref:System.SerializableAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="7ceb9-107">Em vez disso, implementações específicas do .NET, como o .NET Framework e o .NET Core, são livres para determinar se um tipo específico é serializável.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-107">Instead, specific .NET implementations, such as .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="7ceb9-108">Se você tiver desenvolvido uma biblioteca que se destina a .NET Standard, sua biblioteca poderá ser consumida por qualquer implementação do .NET que ofereça suporte a .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-108">If you've developed a library that targets .NET Standard, your library can be consumed by any .NET implementation that supports .NET Standard.</span></span> <span data-ttu-id="7ceb9-109">Isso significa que você não pode saber com antecedência se um tipo específico é serializável; Você só pode determinar se ele é serializável em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="7ceb9-110">Você pode determinar se um objeto é serializável em tempo de execução recuperando o valor da <xref:System.Type.IsSerializable> propriedade de um <xref:System.Type> objeto que representa o tipo desse objeto.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="7ceb9-111">O exemplo a seguir fornece uma implementação.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-111">The following example provides one implementation.</span></span> <span data-ttu-id="7ceb9-112">Ele define um `IsSerializable(Object)` método de extensão que indica se qualquer <xref:System.Object> instância pode ser serializada.</span><span class="sxs-lookup"><span data-stu-id="7ceb9-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="7ceb9-113">Em seguida, você pode passar qualquer objeto para o método para determinar se ele pode ser serializado e desserializado na implementação atual do .NET, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7ceb9-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7ceb9-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="7ceb9-114">See also</span></span>

- [<span data-ttu-id="7ceb9-115">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="7ceb9-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
