---
title: partial (tipo) (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 362a02815cb249d57c0bd19706714df1d71644f4
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929657"
---
# <a name="partial-type-c-reference"></a><span data-ttu-id="38341-102">partial (tipo) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="38341-102">partial (Type) (C# Reference)</span></span>
<span data-ttu-id="38341-103">Definições de tipo parcial permitem que a definição de uma classe, struct ou interface seja dividida em vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="38341-103">Partial type definitions allow for the definition of a class, struct, or interface to be split into multiple files.</span></span>  
  
 <span data-ttu-id="38341-104">Em File1.cs:</span><span class="sxs-lookup"><span data-stu-id="38341-104">In File1.cs:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_1.cs)]  
  
 <span data-ttu-id="38341-105">Em File2.cs, a declaração:</span><span class="sxs-lookup"><span data-stu-id="38341-105">In File2.cs the declaration:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-type_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="38341-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="38341-106">Remarks</span></span>  
 <span data-ttu-id="38341-107">Dividir um tipo de classe, struct ou interface em vários arquivos pode ser útil quando você está trabalhando com projetos grandes ou com o código gerado automaticamente, como o código fornecido pelo [Designer de Formulários do Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="38341-107">Splitting a class, struct or interface type over several files can be useful when you are working with large projects, or with automatically generated code such as that provided by the [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).</span></span> <span data-ttu-id="38341-108">Um tipo parcial pode conter um [método parcial](../../../csharp/language-reference/keywords/partial-method.md).</span><span class="sxs-lookup"><span data-stu-id="38341-108">A partial type may contain a [partial method](../../../csharp/language-reference/keywords/partial-method.md).</span></span> <span data-ttu-id="38341-109">Para obter mais informações, consulte [Classes e métodos parciais](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="38341-109">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="38341-110">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="38341-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="38341-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38341-111">See Also</span></span>

- [<span data-ttu-id="38341-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="38341-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="38341-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="38341-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="38341-114">Modificadores</span><span class="sxs-lookup"><span data-stu-id="38341-114">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="38341-115">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="38341-115">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
