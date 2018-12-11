---
title: Tipo de dados ULong (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 60f39d7bd294a737b5e3c6d5877f5d7e46269dc1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125503"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="08077-102">Tipo de dados ULong (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08077-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="08077-103">Armazena inteiros sem sinal de 64 bits (8 bytes) variando de 0 a 18.446.744.073.709.551.615 (mais de 1,84 vezes 10 ^ 19).</span><span class="sxs-lookup"><span data-stu-id="08077-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08077-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="08077-104">Remarks</span></span>

<span data-ttu-id="08077-105">Use o `ULong` tipo de dados para conter dados binários muito grandes para `UInteger`, ou valores inteiros sem sinal de maior possível.</span><span class="sxs-lookup"><span data-stu-id="08077-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="08077-106">O valor padrão de `ULong` é 0.</span><span class="sxs-lookup"><span data-stu-id="08077-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="08077-107">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="08077-107">Literal assignments</span></span>

<span data-ttu-id="08077-108">Você pode declarar e inicializar um `ULong` variável atribuindo a ela um literal decimal, um literal hexadecimal, um literal octal, ou (começando com o Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="08077-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="08077-109">Se o literal inteiro estiver fora do intervalo de `ULong` (ou seja, se for menor que <xref:System.UInt64.MinValue?displayProperty=nameWithType> ou maior que <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="08077-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="08077-110">No exemplo a seguir, inteiros iguais a 7.934.076.125 representados como literais decimais, hexadecimais e binários são atribuídos a valores `ULong`.</span><span class="sxs-lookup"><span data-stu-id="08077-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="08077-111">Use o prefixo `&h` ou `&H` a fim de denotar um literal hexadecimal, o prefixo `&b` ou `&B` para indicar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="08077-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="08077-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="08077-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="08077-113">Começando com o Visual Basic 2017, você pode também usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="08077-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="08077-114">Começando com o Visual Basic 15.5, você pode também usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos octais, hexadecimais ou binários.</span><span class="sxs-lookup"><span data-stu-id="08077-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="08077-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="08077-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="08077-116">Literais numéricos também podem incluir o `UL` ou `ul` [caractere de tipo](../../programming-guide/language-features/data-types/type-characters.md) para denotar o `ULong` tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="08077-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="08077-117">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="08077-117">Programming tips</span></span>
  
-   <span data-ttu-id="08077-118">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="08077-118">**Negative Numbers.**</span></span> <span data-ttu-id="08077-119">Porque `ULong` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="08077-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="08077-120">Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada para o tipo `ULong`, Visual Basic converte a expressão para `Decimal` primeiro.</span><span class="sxs-lookup"><span data-stu-id="08077-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="08077-121">**Conformidade com CLS.**</span><span class="sxs-lookup"><span data-stu-id="08077-121">**CLS Compliance.**</span></span> <span data-ttu-id="08077-122">O `ULong` tipo de dados não é parte do [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), então um código compatível com CLS não pode consumir um componente que usa-o.</span><span class="sxs-lookup"><span data-stu-id="08077-122">The `ULong` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="08077-123">**Considerações de interoperabilidade.**</span><span class="sxs-lookup"><span data-stu-id="08077-123">**Interop Considerations.**</span></span> <span data-ttu-id="08077-124">Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, tenha em mente que tipos como `ulong` pode ter uma largura de dados diferente (32 bits) em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="08077-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="08077-125">Se você estiver passando um argumento de 32 bits para tal componente, declare-o como `UInteger` em vez de `ULong` no seu código gerenciado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="08077-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="08077-126">Além disso, automação não dá suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000.</span><span class="sxs-lookup"><span data-stu-id="08077-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="08077-127">Você não pode passar um Visual Basic `ULong` argumento para um componente de automação nessas plataformas.</span><span class="sxs-lookup"><span data-stu-id="08077-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="08077-128">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="08077-128">**Widening.**</span></span> <span data-ttu-id="08077-129">O `ULong` tipo de dados amplia a `Decimal`, `Single`, e `Double`.</span><span class="sxs-lookup"><span data-stu-id="08077-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="08077-130">Isso significa que você pode converter `ULong` para qualquer um desses tipos sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="08077-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="08077-131">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="08077-131">**Type Characters.**</span></span> <span data-ttu-id="08077-132">Acrescentar os caracteres de tipo literal `UL` a um literal o força ao `ULong` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="08077-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="08077-133">`ULong` não tem nenhum caractere de tipo de identificador.</span><span class="sxs-lookup"><span data-stu-id="08077-133">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="08077-134">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="08077-134">**Framework Type.**</span></span> <span data-ttu-id="08077-135">O tipo correspondente no .NET Framework é a estrutura <xref:System.UInt64?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="08077-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08077-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08077-136">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="08077-137">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="08077-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="08077-138">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="08077-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="08077-139">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="08077-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="08077-140">Como: Chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="08077-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="08077-141">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="08077-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
