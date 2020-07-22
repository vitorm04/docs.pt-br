---
title: Construtores particulares – Guia de Programação em C#
description: Um Construtor privado é um construtor de instância especial em C# usado para restringir como um objeto pode ser criado. Eles podem ser usados com métodos de fábrica ou outros idiomas de construção.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: a6b86ccb870da0262bcbc516e176e00d17724f9f
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864053"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="8bc69-104">Construtores particulares (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8bc69-104">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="8bc69-105">Um construtor particular é um construtor de instância especial.</span><span class="sxs-lookup"><span data-stu-id="8bc69-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="8bc69-106">Normalmente, ele é usado em classes que contêm apenas membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="8bc69-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="8bc69-107">Se uma classe tiver um ou mais construtores particulares e nenhum construtor público, outras classes (exceto as classes aninhadas) não poderão criar instâncias dessa classe.</span><span class="sxs-lookup"><span data-stu-id="8bc69-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="8bc69-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8bc69-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="8bc69-109">A declaração do construtor vazio impede a geração automática de um construtor sem parâmetro.</span><span class="sxs-lookup"><span data-stu-id="8bc69-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="8bc69-110">Observe que, se você não usar um modificador de acesso com o construtor, ele ainda será privado por padrão.</span><span class="sxs-lookup"><span data-stu-id="8bc69-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="8bc69-111">No entanto, o modificador [private](../../language-reference/keywords/private.md) geralmente é usado explicitamente para deixar claro que a classe não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="8bc69-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="8bc69-112">Construtores particulares são usados para impedir a criação de instâncias de uma classe quando não há métodos ou campos de instância, como a classe <xref:System.Math> ou quando um método é chamado para obter uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="8bc69-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="8bc69-113">Se todos os métodos na classe forem estáticos, considere deixar toda a classe estática.</span><span class="sxs-lookup"><span data-stu-id="8bc69-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="8bc69-114">Para obter mais informações [, consulte classes estáticas e membros de classe estática](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="8bc69-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bc69-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8bc69-115">Example</span></span>  
 <span data-ttu-id="8bc69-116">A seguir, temos um exemplo de uma classe usando um construtor particular.</span><span class="sxs-lookup"><span data-stu-id="8bc69-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="8bc69-117">Observe que se você remover a marca de comentário da seguinte instrução do exemplo, ela gerará um erro porque o construtor está inacessível devido a seu nível de proteção:</span><span class="sxs-lookup"><span data-stu-id="8bc69-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8bc69-118">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8bc69-118">C# Language Specification</span></span>  

<span data-ttu-id="8bc69-119">Para obter mais informações, veja [Construtores privados](~/_csharplang/spec/classes.md#private-constructors) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="8bc69-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="8bc69-120">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="8bc69-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8bc69-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="8bc69-121">See also</span></span>

- [<span data-ttu-id="8bc69-122">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8bc69-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8bc69-123">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="8bc69-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="8bc69-124">Construtores</span><span class="sxs-lookup"><span data-stu-id="8bc69-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="8bc69-125">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="8bc69-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="8bc69-126">pessoal</span><span class="sxs-lookup"><span data-stu-id="8bc69-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="8bc69-127">público</span><span class="sxs-lookup"><span data-stu-id="8bc69-127">public</span></span>](../../language-reference/keywords/public.md)
