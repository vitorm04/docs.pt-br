---
title: Tipo de dados Byte (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b106005ff07f55e05ae66dba94041cd8b5c24bb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750174"
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="296dc-102">Tipo de dados byte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="296dc-102">Byte data type (Visual Basic)</span></span>
<span data-ttu-id="296dc-103">Armazena inteiros sem sinal de 8 bits (1-bytes) que variam em valor de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="296dc-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="296dc-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="296dc-104">Remarks</span></span>

<span data-ttu-id="296dc-105">Use o `Byte` tipo de dados para conter dados binários.</span><span class="sxs-lookup"><span data-stu-id="296dc-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="296dc-106">O valor padrão de `Byte` é 0.</span><span class="sxs-lookup"><span data-stu-id="296dc-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="296dc-107">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="296dc-107">Literal assignments</span></span>

<span data-ttu-id="296dc-108">Você pode declarar e inicializar um `Byte` variável atribuindo a ela um literal decimal, um literal hexadecimal, um literal octal, ou (começando com o Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="296dc-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="296dc-109">Se o literal inteiro estiver fora do intervalo de um `Byte` (ou seja, se ele for menor que <xref:System.Byte.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Byte.MaxValue?displayProperty=nameWithType>), ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="296dc-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="296dc-110">No exemplo a seguir, inteiros iguais a 201 representados como decimais, hexadecimais e literais binários são implicitamente convertidos de [inteiro](integer-data-type.md) para `byte` valores.</span><span class="sxs-lookup"><span data-stu-id="296dc-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="296dc-111">Use o prefixo `&h` ou `&H` a fim de denotar um literal hexadecimal, o prefixo `&b` ou `&B` para indicar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="296dc-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="296dc-112">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="296dc-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="296dc-113">Começando com o Visual Basic 2017, você pode também usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="296dc-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

<span data-ttu-id="296dc-114">Começando com o Visual Basic 15.5, você pode também usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos octais, hexadecimais ou binários.</span><span class="sxs-lookup"><span data-stu-id="296dc-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="296dc-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="296dc-115">For example:</span></span>

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a><span data-ttu-id="296dc-116">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="296dc-116">Programming tips</span></span>

-   <span data-ttu-id="296dc-117">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="296dc-117">**Negative Numbers.**</span></span> <span data-ttu-id="296dc-118">Porque `Byte` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="296dc-118">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="296dc-119">Se você usar o operador unário menos (`-`) ou uma expressão que é avaliada para o tipo `Byte`, Visual Basic converte a expressão para `Short` primeiro.</span><span class="sxs-lookup"><span data-stu-id="296dc-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
-   <span data-ttu-id="296dc-120">**Conversões de formato.**</span><span class="sxs-lookup"><span data-stu-id="296dc-120">**Format Conversions.**</span></span> <span data-ttu-id="296dc-121">Quando o Visual Basic lê ou grava arquivos, ou quando ele chamar DLLs, métodos e propriedades, ele pode converter entre formatos de dados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="296dc-121">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="296dc-122">Dados binários armazenados em `Byte` matrizes e variáveis são preservados durante essas conversões de formato.</span><span class="sxs-lookup"><span data-stu-id="296dc-122">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="296dc-123">Você não deve usar um `String` variável para dados binários, porque seu conteúdo pode estar corrompido durante a conversão entre os formatos ANSI e Unicode.</span><span class="sxs-lookup"><span data-stu-id="296dc-123">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

-   <span data-ttu-id="296dc-124">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="296dc-124">**Widening.**</span></span> <span data-ttu-id="296dc-125">O `Byte` tipo de dados amplia a `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="296dc-125">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="296dc-126">Isso significa que você pode converter `Byte` para qualquer um desses tipos sem encontrar uma <xref:System.OverflowException?displayProperty=nameWithType> erro.</span><span class="sxs-lookup"><span data-stu-id="296dc-126">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="296dc-127">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="296dc-127">**Type Characters.**</span></span> <span data-ttu-id="296dc-128">`Byte` não tem nenhum caractere de tipo literal ou um caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="296dc-128">`Byte` has no literal type character or identifier type character.</span></span>

-   <span data-ttu-id="296dc-129">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="296dc-129">**Framework Type.**</span></span> <span data-ttu-id="296dc-130">O tipo correspondente no .NET Framework é a estrutura <xref:System.Byte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="296dc-130">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="296dc-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="296dc-131">Example</span></span>

 <span data-ttu-id="296dc-132">No exemplo a seguir `b` é um `Byte` variável.</span><span class="sxs-lookup"><span data-stu-id="296dc-132">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="296dc-133">As instruções demonstram o intervalo da variável e a aplicação de operadores bit shift a ele.</span><span class="sxs-lookup"><span data-stu-id="296dc-133">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a><span data-ttu-id="296dc-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="296dc-134">See Also</span></span>

 <xref:System.Byte?displayProperty=nameWithType>  
 [<span data-ttu-id="296dc-135">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="296dc-135">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="296dc-136">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="296dc-136">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="296dc-137">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="296dc-137">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="296dc-138">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="296dc-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
