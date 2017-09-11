---
title: Tipo de dados byte (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Byte
dev_langs:
- VB
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3d3eb44f79ecfb18a914b6f01424950bc648c0fe
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="d2963-102">Tipo de dados Byte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2963-102">Byte Data Type (Visual Basic)</span></span>
<span data-ttu-id="d2963-103">Armazena inteiros de (1 byte) de 8 bits sem sinal que variam em valor de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="d2963-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2963-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2963-104">Remarks</span></span>  
 <span data-ttu-id="d2963-105">Use o `Byte` tipo de dados para armazenar dados binários.</span><span class="sxs-lookup"><span data-stu-id="d2963-105">Use the `Byte` data type to contain binary data.</span></span>  
  
 <span data-ttu-id="d2963-106">O valor padrão de `Byte` é 0.</span><span class="sxs-lookup"><span data-stu-id="d2963-106">The default value of `Byte` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="d2963-107">Dicas de programação</span><span class="sxs-lookup"><span data-stu-id="d2963-107">Programming Tips</span></span>  
  
-   <span data-ttu-id="d2963-108">**Números negativos.**</span><span class="sxs-lookup"><span data-stu-id="d2963-108">**Negative Numbers.**</span></span> <span data-ttu-id="d2963-109">Porque `Byte` é um tipo sem sinal, ele não pode representar um número negativo.</span><span class="sxs-lookup"><span data-stu-id="d2963-109">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="d2963-110">Se você usar o operador unário menos (`-`) ou uma expressão avaliada como tipo `Byte`, Visual Basic converte a expressão para `Short` primeiro.</span><span class="sxs-lookup"><span data-stu-id="d2963-110">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>  
  
-   <span data-ttu-id="d2963-111">**Conversões de formato.**</span><span class="sxs-lookup"><span data-stu-id="d2963-111">**Format Conversions.**</span></span> <span data-ttu-id="d2963-112">Quando o Visual Basic lê ou grava arquivos, ou quando ele chama DLLs, métodos e propriedades, pode converter automaticamente entre os formatos de dados.</span><span class="sxs-lookup"><span data-stu-id="d2963-112">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="d2963-113">Dados binários armazenados em `Byte` matrizes e variáveis são preservados durante essas conversões de formato.</span><span class="sxs-lookup"><span data-stu-id="d2963-113">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="d2963-114">Você não deve usar um `String` variável para dados binários, porque seu conteúdo pode ser corrompido durante a conversão entre ANSI e Unicode formatos.</span><span class="sxs-lookup"><span data-stu-id="d2963-114">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>  
  
-   <span data-ttu-id="d2963-115">**Ampliação.**</span><span class="sxs-lookup"><span data-stu-id="d2963-115">**Widening.**</span></span> <span data-ttu-id="d2963-116">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span><span class="sxs-lookup"><span data-stu-id="d2963-116">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="d2963-117">Isso significa que você pode converter `Byte` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d2963-117">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=fullName> error.</span></span>  
  
-   <span data-ttu-id="d2963-118">**Caracteres de tipo.**</span><span class="sxs-lookup"><span data-stu-id="d2963-118">**Type Characters.**</span></span> <span data-ttu-id="d2963-119">`Byte`não possui caractere de tipo literal ou caractere de tipo identificador.</span><span class="sxs-lookup"><span data-stu-id="d2963-119">`Byte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="d2963-120">**Tipo de estrutura.**</span><span class="sxs-lookup"><span data-stu-id="d2963-120">**Framework Type.**</span></span> <span data-ttu-id="d2963-121">O tipo correspondente no .NET Framework é o <xref:System.Byte?displayProperty=fullName>estrutura.</xref:System.Byte?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d2963-121">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=fullName> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2963-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2963-122">Example</span></span>  
 <span data-ttu-id="d2963-123">No exemplo a seguir, `b` é um `Byte` variável.</span><span class="sxs-lookup"><span data-stu-id="d2963-123">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="d2963-124">As instruções demonstram o intervalo da variável e a aplicação de operadores bit shift para ele.</span><span class="sxs-lookup"><span data-stu-id="d2963-124">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>  
  
 <span data-ttu-id="d2963-125">[!code-vb[VbVbalrDataTypes n º&16;](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d2963-125">[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2963-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2963-126">See Also</span></span>  
 <span data-ttu-id="d2963-127"><xref:System.Byte?displayProperty=fullName></xref:System.Byte?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d2963-127"><xref:System.Byte?displayProperty=fullName></span></span>   
<span data-ttu-id="d2963-128"> [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="d2963-128"> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="d2963-129"> [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="d2963-129"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="d2963-130"> [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="d2963-130"> [Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
<span data-ttu-id="d2963-131"> [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="d2963-131"> [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
