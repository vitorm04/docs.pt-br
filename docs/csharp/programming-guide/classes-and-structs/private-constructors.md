---
title: Construtores particulares – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705438"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="75400-102">Construtores particulares (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="75400-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="75400-103">Um construtor particular é um construtor de instância especial.</span><span class="sxs-lookup"><span data-stu-id="75400-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="75400-104">Normalmente, ele é usado em classes que contêm apenas membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="75400-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="75400-105">Se uma classe tiver um ou mais construtores particulares e nenhum construtor público, outras classes (exceto as classes aninhadas) não poderão criar instâncias dessa classe.</span><span class="sxs-lookup"><span data-stu-id="75400-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="75400-106">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="75400-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="75400-107">A declaração do construtor vazio impede a geração automática de um construtor sem parâmetro.</span><span class="sxs-lookup"><span data-stu-id="75400-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="75400-108">Observe que, se você não usar um modificador de acesso com o construtor, ele ainda será privado por padrão.</span><span class="sxs-lookup"><span data-stu-id="75400-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="75400-109">No entanto, o modificador [private](../../language-reference/keywords/private.md) geralmente é usado explicitamente para deixar claro que a classe não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="75400-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="75400-110">Construtores particulares são usados para impedir a criação de instâncias de uma classe quando não há métodos ou campos de instância, como a classe <xref:System.Math> ou quando um método é chamado para obter uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="75400-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="75400-111">Se todos os métodos na classe forem estáticos, considere deixar toda a classe estática.</span><span class="sxs-lookup"><span data-stu-id="75400-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="75400-112">Para obter mais informações, consulte [Classes Estáticas e Membros de Classe Estática](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="75400-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75400-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="75400-113">Example</span></span>  
 <span data-ttu-id="75400-114">A seguir, temos um exemplo de uma classe usando um construtor particular.</span><span class="sxs-lookup"><span data-stu-id="75400-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="75400-115">Observe que se você remover a marca de comentário da seguinte instrução do exemplo, ela gerará um erro porque o construtor está inacessível devido a seu nível de proteção:</span><span class="sxs-lookup"><span data-stu-id="75400-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="75400-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="75400-116">C# Language Specification</span></span>  

<span data-ttu-id="75400-117">Para obter mais informações, veja [Construtores privados](~/_csharplang/spec/classes.md#private-constructors) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="75400-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="75400-118">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="75400-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="75400-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="75400-119">See also</span></span>

- [<span data-ttu-id="75400-120">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="75400-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="75400-121">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="75400-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="75400-122">Construtores</span><span class="sxs-lookup"><span data-stu-id="75400-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="75400-123">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="75400-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="75400-124">Privada</span><span class="sxs-lookup"><span data-stu-id="75400-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="75400-125">público</span><span class="sxs-lookup"><span data-stu-id="75400-125">public</span></span>](../../language-reference/keywords/public.md)
