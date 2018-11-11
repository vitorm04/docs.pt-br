---
title: Tipo de dados UShort (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
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
ms.openlocfilehash: a3d60747400d570a3e5a930377e9be9c0aca4f35
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982705"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="4ef4d-102">Tipo de dados UShort (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ef4d-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="4ef4d-103">Armazena inteiros sem sinal de 16 bits (2 bytes) que variam de 0 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ef4d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ef4d-104">Remarks</span></span>

 <span data-ttu-id="4ef4d-105">Use o `UShort` tipo de dados para conter dados binários muito grandes para `Byte`.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="4ef4d-106">O valor padrão de `UShort` é 0.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="4ef4d-107">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="4ef4d-107">Literal assignments</span></span>

<span data-ttu-id="4ef4d-108">Você pode declarar e inicializar um `UShort` variável atribuindo a ela um literal decimal, um literal hexadecimal, um literal octal, ou (começando com o Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="4ef4d-109">Se o literal inteiro estiver fora do intervalo de `UShort` (ou seja, se for menor que <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="4ef4d-110">No exemplo a seguir, inteiros iguais a 65.034 representados como decimais, hexadecimais e literais binários são atribuídos a `UShort` valores.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="4ef4d-111">Use o prefixo `&h` ou `&H` a fim de denotar um literal hexadecimal, o prefixo `&b` ou `&B` para indicar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4ef4d-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4ef4d-113">Começando com o Visual Basic 2017, você pode também usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="4ef4d-114">Começando com o Visual Basic 15.5, você pode também usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos octais, hexadecimais ou binários.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4ef4d-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4ef4d-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4ef4d-116">Literais numéricos também podem incluir o `US` ou `us` [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o `UShort` tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="4ef4d-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="4ef4d-117">Programming tips</span></span>
  
-   <span data-ttu-id="4ef4d-118">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="4ef4d-118">**Negative Numbers.**</span></span> <span data-ttu-id="4ef4d-119">Porque `UShort` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="4ef4d-120">Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada para o tipo `UShort`, Visual Basic converte a expressão para `Integer` primeiro.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="4ef4d-121">**Conformidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="4ef4d-121">**CLS Compliance.**</span></span> <span data-ttu-id="4ef4d-122">O `UShort` tipo de dados não é parte do [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), então um código compatível com CLS não pode consumir um componente que usa-o.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="4ef4d-123">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="4ef4d-123">**Widening.**</span></span> <span data-ttu-id="4ef4d-124">O `UShort` tipo de dados amplia a `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, e `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="4ef4d-125">Isso significa que você pode converter `UShort` para qualquer um desses tipos sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="4ef4d-126">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="4ef4d-126">**Type Characters.**</span></span> <span data-ttu-id="4ef4d-127">Acrescentar os caracteres de tipo literal `US` a um literal o força ao `UShort` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="4ef4d-128">`UShort` não tem nenhum caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="4ef4d-129">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="4ef4d-129">**Framework Type.**</span></span> <span data-ttu-id="4ef4d-130">O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ef4d-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef4d-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ef4d-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="4ef4d-132">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4ef4d-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="4ef4d-133">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="4ef4d-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="4ef4d-134">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="4ef4d-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="4ef4d-135">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="4ef4d-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="4ef4d-136">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4ef4d-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
