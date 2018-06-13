---
title: implicit (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215011"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="0a6f0-102">implicit (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0a6f0-102">implicit (C# Reference)</span></span>
<span data-ttu-id="0a6f0-103">A palavra-chave `implicit` é usada para declarar um operador de conversão implícita de tipo definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0a6f0-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="0a6f0-104">Use-a para habilitar conversões implícitas entre um tipo definido pelo usuário e outro tipo, se houver garantia de que a conversão não causará perda de dados.</span><span class="sxs-lookup"><span data-stu-id="0a6f0-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a6f0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0a6f0-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="0a6f0-106">Com a eliminação de conversões desnecessárias, as conversões implícitas podem melhorar a legibilidade do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="0a6f0-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="0a6f0-107">No entanto, como as conversões implícitas não exigem que os programadores convertam explicitamente de um tipo para outro, é necessário ter cuidado para evitar resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="0a6f0-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="0a6f0-108">De modo geral, operadores de conversão implícita nunca devem gerar exceções e perder informações, para que possam ser usados com segurança sem conhecimento do programador.</span><span class="sxs-lookup"><span data-stu-id="0a6f0-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="0a6f0-109">Se um operador de conversão não puder atender a esses critérios, ele deve ser marcado como `explicit`.</span><span class="sxs-lookup"><span data-stu-id="0a6f0-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="0a6f0-110">Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0a6f0-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0a6f0-111">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0a6f0-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a6f0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a6f0-112">See Also</span></span>  
 [<span data-ttu-id="0a6f0-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0a6f0-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0a6f0-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0a6f0-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0a6f0-115">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0a6f0-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0a6f0-116">explicit</span><span class="sxs-lookup"><span data-stu-id="0a6f0-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="0a6f0-117">operator (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0a6f0-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="0a6f0-118">Como implementar conversões definidas pelo usuário entre structs</span><span class="sxs-lookup"><span data-stu-id="0a6f0-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
