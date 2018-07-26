---
title: object (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199245"
---
# <a name="object-c-reference"></a><span data-ttu-id="9eaee-102">object (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9eaee-102">object (C# Reference)</span></span>
<span data-ttu-id="9eaee-103">O tipo `object` é um alias para <xref:System.Object> no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9eaee-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="9eaee-104">No sistema de tipos unificado do C#, todos os tipos, predefinidos e definidos pelo usuário, tipos de referência e tipos de valor, herdam direta ou indiretamente de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9eaee-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="9eaee-105">Você pode atribuir valores de qualquer tipo a variáveis do tipo `object`.</span><span class="sxs-lookup"><span data-stu-id="9eaee-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="9eaee-106">Quando uma variável de um tipo de valor é convertida para um objeto, ela é chamada de *boxed*.</span><span class="sxs-lookup"><span data-stu-id="9eaee-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="9eaee-107">Quando uma variável do objeto do tipo é convertida para um tipo de valor, ela é chamada de *unboxed*.</span><span class="sxs-lookup"><span data-stu-id="9eaee-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="9eaee-108">Para obter mais informações, consulte [Boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="9eaee-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eaee-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9eaee-109">Example</span></span>  
 <span data-ttu-id="9eaee-110">O exemplo a seguir mostra como variáveis do tipo `object` podem aceitar valores de qualquer tipo de dados e como as variáveis do tipo `object` pode usar métodos <xref:System.Object> do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9eaee-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9eaee-111">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9eaee-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9eaee-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9eaee-112">See Also</span></span>  
 [<span data-ttu-id="9eaee-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9eaee-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9eaee-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9eaee-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9eaee-115">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="9eaee-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9eaee-116">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="9eaee-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="9eaee-117">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="9eaee-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
