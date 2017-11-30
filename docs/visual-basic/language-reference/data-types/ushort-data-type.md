---
title: Tipo de dados UShort (Visual Basic)
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513e8ce4694788d33c5aa14e34b95e88b6d37ff1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="b4e47-102">Tipo de dados UShort (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4e47-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="b4e47-103">Mantém inteiros sem sinal 16 bits (2 bytes) que variam de 0 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="b4e47-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4e47-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4e47-104">Remarks</span></span>

 <span data-ttu-id="b4e47-105">Use o `UShort` tipo de dados para conter dados binários muito grandes para `Byte`.</span><span class="sxs-lookup"><span data-stu-id="b4e47-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="b4e47-106">O valor padrão de `UShort` é 0.</span><span class="sxs-lookup"><span data-stu-id="b4e47-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="b4e47-107">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="b4e47-107">Literal assignments</span></span>

<span data-ttu-id="b4e47-108">Você pode declarar e inicializar uma `UShort` variável atribuindo a ele um literal decimal, hexadecimal literal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="b4e47-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="b4e47-109">Se o literal inteiro estiver fora do intervalo de `UShort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="b4e47-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="b4e47-110">No exemplo a seguir, inteiros igual à 65,034 que são representados como decimal, hexadecimal, e literais binárias são atribuídas a `UShort` valores.</span><span class="sxs-lookup"><span data-stu-id="b4e47-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="b4e47-111">Use o prefixo `&h` ou `&H` para denotar um hexadecimal literal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="b4e47-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="b4e47-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="b4e47-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="b4e47-113">A partir do Visual Basic de 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígito para melhorar a legibilidade, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="b4e47-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="b4e47-114">Literais numéricos também podem incluir o `US` ou `us` [caractere de tipo](../../programming-guide\language-features\data-types/type-characters.md) para denotar o `UShort` tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4e47-114">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H035826us
```

## <a name="programming-tips"></a><span data-ttu-id="b4e47-115">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="b4e47-115">Programming tips</span></span>
  
-   <span data-ttu-id="b4e47-116">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="b4e47-116">**Negative Numbers.**</span></span> <span data-ttu-id="b4e47-117">Porque `UShort` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="b4e47-117">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="b4e47-118">Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada como tipo `UShort`, Visual Basic converte a expressão a ser `Integer` primeiro.</span><span class="sxs-lookup"><span data-stu-id="b4e47-118">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="b4e47-119">**Compatibilidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="b4e47-119">**CLS Compliance.**</span></span> <span data-ttu-id="b4e47-120">O `UShort` tipo de dados não é parte do [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), então um código compatível com CLS não pode consumir um componente que usa.</span><span class="sxs-lookup"><span data-stu-id="b4e47-120">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="b4e47-121">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="b4e47-121">**Widening.**</span></span> <span data-ttu-id="b4e47-122">O `UShort` tipo de dados amplia a `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, e `Double`.</span><span class="sxs-lookup"><span data-stu-id="b4e47-122">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="b4e47-123">Isso significa que você pode converter `UShort` para qualquer um desses tipos sem encontrar um <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="b4e47-123">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="b4e47-124">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="b4e47-124">**Type Characters.**</span></span> <span data-ttu-id="b4e47-125">Acrescentar os caracteres de tipo literal `US` para um literal força-o `UShort` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b4e47-125">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="b4e47-126">`UShort`não tem nenhum caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="b4e47-126">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="b4e47-127">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="b4e47-127">**Framework Type.**</span></span> <span data-ttu-id="b4e47-128">O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4e47-128">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e47-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4e47-129">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="b4e47-130">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="b4e47-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="b4e47-131">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="b4e47-131">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="b4e47-132">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="b4e47-132">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="b4e47-133">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="b4e47-133">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="b4e47-134">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="b4e47-134">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
