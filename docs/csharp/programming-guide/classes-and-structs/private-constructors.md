---
title: Construtores particulares – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: faa5132845a2d463d3b7d74dc0e0cce21dca61aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596218"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="71020-102">Construtores particulares (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="71020-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="71020-103">Um construtor particular é um construtor de instância especial.</span><span class="sxs-lookup"><span data-stu-id="71020-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="71020-104">Normalmente, ele é usado em classes que contêm apenas membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="71020-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="71020-105">Se uma classe tiver um ou mais construtores particulares e nenhum construtor público, outras classes (exceto as classes aninhadas) não poderão criar instâncias dessa classe.</span><span class="sxs-lookup"><span data-stu-id="71020-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="71020-106">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="71020-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="71020-107">A declaração do construtor vazio impede a geração automática de um construtor sem parâmetro.</span><span class="sxs-lookup"><span data-stu-id="71020-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="71020-108">Observe que, se você não usar um modificador de acesso com o construtor, ele ainda será privado por padrão.</span><span class="sxs-lookup"><span data-stu-id="71020-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="71020-109">No entanto, o modificador [private](../../language-reference/keywords/private.md) geralmente é usado explicitamente para deixar claro que a classe não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="71020-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="71020-110">Construtores particulares são usados para impedir a criação de instâncias de uma classe quando não há métodos ou campos de instância, como a classe <xref:System.Math> ou quando um método é chamado para obter uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="71020-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="71020-111">Se todos os métodos na classe forem estáticos, considere deixar toda a classe estática.</span><span class="sxs-lookup"><span data-stu-id="71020-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="71020-112">Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="71020-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71020-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71020-113">Example</span></span>  
 <span data-ttu-id="71020-114">A seguir, temos um exemplo de uma classe usando um construtor particular.</span><span class="sxs-lookup"><span data-stu-id="71020-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="71020-115">Observe que se você remover a marca de comentário da seguinte instrução do exemplo, ela gerará um erro porque o construtor está inacessível devido a seu nível de proteção:</span><span class="sxs-lookup"><span data-stu-id="71020-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="71020-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="71020-116">C# Language Specification</span></span>  

<span data-ttu-id="71020-117">Para obter mais informações, veja [Construtores privados](~/_csharplang/spec/classes.md#private-constructors) na [Especificação da Linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="71020-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="71020-118">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="71020-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="71020-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71020-119">See also</span></span>

- [<span data-ttu-id="71020-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="71020-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="71020-121">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="71020-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="71020-122">Construtores</span><span class="sxs-lookup"><span data-stu-id="71020-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="71020-123">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="71020-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="71020-124">private</span><span class="sxs-lookup"><span data-stu-id="71020-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="71020-125">public</span><span class="sxs-lookup"><span data-stu-id="71020-125">public</span></span>](../../language-reference/keywords/public.md)
