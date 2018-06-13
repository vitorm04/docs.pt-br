---
title: Tipo de dados curto (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: ef99743828d8d80844486b651178622ff45fd554
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590706"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="4209b-102">Tipo de dados curto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4209b-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="4209b-103">Armazena inteiros de 16 bits (2 bytes) que variam de -32.768 a 32.767.</span><span class="sxs-lookup"><span data-stu-id="4209b-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4209b-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="4209b-104">Remarks</span></span>  
 <span data-ttu-id="4209b-105">Use o `Short` tipo de dados para conter valores inteiros que não requerem a largura total de dados de `Integer`.</span><span class="sxs-lookup"><span data-stu-id="4209b-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="4209b-106">Em alguns casos, o common language runtime pode empacotar sua `Short` variáveis próximas uma da outra e economizar memória.</span><span class="sxs-lookup"><span data-stu-id="4209b-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="4209b-107">O valor padrão de `Short` é 0.</span><span class="sxs-lookup"><span data-stu-id="4209b-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="4209b-108">Atribuições de literal</span><span class="sxs-lookup"><span data-stu-id="4209b-108">Literal assignments</span></span>

<span data-ttu-id="4209b-109">Você pode declarar e inicializar uma `Short` variável atribuindo a ele um literal decimal, hexadecimal literal, um literal octal, ou (começando com Visual Basic 2017) um literal binário.</span><span class="sxs-lookup"><span data-stu-id="4209b-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="4209b-110">Se o literal inteiro estiver fora do intervalo de `Short` (ou seja, se for menor que <xref:System.Int16.MinValue?displayProperty=nameWithType> ou maior que <xref:System.Int16.MaxValue?displayProperty=nameWithType>, ocorrerá um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="4209b-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="4209b-111">No exemplo a seguir, inteiros igual à 1,034 que são representados como decimal, hexadecimal, e literais binárias são implicitamente convertidos do [inteiro](integer-data-type.md) para `Short` valores.</span><span class="sxs-lookup"><span data-stu-id="4209b-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="4209b-112">Use o prefixo `&h` ou `&H` para denotar um hexadecimal literal, o prefixo `&b` ou `&B` para denotar um literal binário e o prefixo `&o` ou `&O` para denotar um literal octal.</span><span class="sxs-lookup"><span data-stu-id="4209b-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="4209b-113">Literais decimais não têm nenhum prefixo.</span><span class="sxs-lookup"><span data-stu-id="4209b-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="4209b-114">A partir do Visual Basic de 2017, você também pode usar o caractere de sublinhado, `_`, como um separador de dígito para melhorar a legibilidade, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="4209b-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="4209b-115">A partir do Visual Basic 15,5, você também pode usar o caractere de sublinhado (`_`) como um separador à esquerda entre o prefixo e os dígitos hexadecimais, binários ou octais.</span><span class="sxs-lookup"><span data-stu-id="4209b-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="4209b-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="4209b-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="4209b-117">Literais numéricos também podem incluir o `S` [caractere de tipo](../../programming-guide\language-features\data-types/type-characters.md) para denotar o `Short` tipo de dados, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4209b-117">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="4209b-118">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="4209b-118">Programming tips</span></span>

-   <span data-ttu-id="4209b-119">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="4209b-119">**Widening.**</span></span> <span data-ttu-id="4209b-120">O `Short` tipo de dados amplia a `Integer`, `Long`, `Decimal`, `Single`, ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="4209b-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="4209b-121">Isso significa que você pode converter `Short` em qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4209b-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="4209b-122">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="4209b-122">**Type Characters.**</span></span> <span data-ttu-id="4209b-123">Acrescentar o caractere de tipo literal `S` a um literal o força ao tipo de dados `Short`.</span><span class="sxs-lookup"><span data-stu-id="4209b-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="4209b-124">`Short` não tem nenhum caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="4209b-124">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="4209b-125">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="4209b-125">**Framework Type.**</span></span> <span data-ttu-id="4209b-126">O tipo correspondente no .NET Framework é a estrutura <xref:System.Int16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4209b-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4209b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4209b-127">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="4209b-128">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4209b-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="4209b-129">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="4209b-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="4209b-130">Resumo da Conversão</span><span class="sxs-lookup"><span data-stu-id="4209b-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="4209b-131">Tipo de Dados Integer</span><span class="sxs-lookup"><span data-stu-id="4209b-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="4209b-132">Tipo de Dados Long</span><span class="sxs-lookup"><span data-stu-id="4209b-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="4209b-133">Uso Eficiente de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4209b-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
