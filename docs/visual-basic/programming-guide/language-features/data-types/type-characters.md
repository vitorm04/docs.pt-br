---
title: Caracteres de tipo (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bd017db40fc28c78e960a889947cc7323e3e156
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="16af3-102">Digite os caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16af3-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="16af3-103">Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação com um *caractere de tipo*.</span><span class="sxs-lookup"><span data-stu-id="16af3-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="16af3-104">O caractere de tipo deve seguir imediatamente o elemento, com nenhum caractere intermediário de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="16af3-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="16af3-105">O caractere de tipo não é parte do nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="16af3-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="16af3-106">Um elemento definido com um caractere de tipo pode ser referenciado sem o caractere de tipo.</span><span class="sxs-lookup"><span data-stu-id="16af3-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="16af3-107">Caracteres de tipo identificador</span><span class="sxs-lookup"><span data-stu-id="16af3-107">Identifier type characters</span></span>

<span data-ttu-id="16af3-108">Visual Basic fornece um conjunto de *caracteres de tipo identificador* que você pode usar em uma declaração para especificar o tipo de dados de uma variável ou constante.</span><span class="sxs-lookup"><span data-stu-id="16af3-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="16af3-109">A tabela a seguir mostra os caracteres de tipo identificador disponíveis com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="16af3-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="16af3-110">Caractere de tipo identificador</span><span class="sxs-lookup"><span data-stu-id="16af3-110">Identifier type character</span></span>|<span data-ttu-id="16af3-111">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="16af3-111">Data type</span></span>|<span data-ttu-id="16af3-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16af3-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="16af3-113">Nenhum caractere de tipo identificador existe para o `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort` tipos de dados, ou para qualquer um tipos de dados compostos, como arrays ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="16af3-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="16af3-114">Em alguns casos, você pode acrescentar o `$` de caracteres para uma função do Visual Basic, por exemplo `Left$` em vez de `Left`, para obter um valor retornado do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="16af3-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="16af3-115">Em todos os casos, o caractere de tipo identificador deve seguir imediatamente o nome do identificador.</span><span class="sxs-lookup"><span data-stu-id="16af3-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="16af3-116">Caracteres de tipo literal</span><span class="sxs-lookup"><span data-stu-id="16af3-116">Literal type characters</span></span>

<span data-ttu-id="16af3-117">Um *literal* é uma representação textual de um determinado valor de um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="16af3-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="16af3-118">Tipos de literal padrão</span><span class="sxs-lookup"><span data-stu-id="16af3-118">Default literal types</span></span>

<span data-ttu-id="16af3-119">A forma de um literal como ele aparece no seu código normalmente determina seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="16af3-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="16af3-120">A tabela a seguir mostra esses tipos padrão.</span><span class="sxs-lookup"><span data-stu-id="16af3-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="16af3-121">Formato textual de literal</span><span class="sxs-lookup"><span data-stu-id="16af3-121">Textual form of literal</span></span>|<span data-ttu-id="16af3-122">Tipo de dados padrão</span><span class="sxs-lookup"><span data-stu-id="16af3-122">Default data type</span></span>|<span data-ttu-id="16af3-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16af3-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="16af3-124">Numérico, sem parte fracionária</span><span class="sxs-lookup"><span data-stu-id="16af3-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="16af3-125">Numérico, sem parte fracionária, muito grande para`Integer`</span><span class="sxs-lookup"><span data-stu-id="16af3-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="16af3-126">Numérico, parte fracionária</span><span class="sxs-lookup"><span data-stu-id="16af3-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="16af3-127">Entre aspas duplas</span><span class="sxs-lookup"><span data-stu-id="16af3-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="16af3-128">Entre sinais numéricos</span><span class="sxs-lookup"><span data-stu-id="16af3-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="16af3-129">Tipos literais forçados</span><span class="sxs-lookup"><span data-stu-id="16af3-129">Forced literal types</span></span>

<span data-ttu-id="16af3-130">Visual Basic fornece um conjunto de *caracteres de tipo literal*, indicando que você pode usar para forçar um literal a assumir um tipo de dados diferente do seu formulário.</span><span class="sxs-lookup"><span data-stu-id="16af3-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="16af3-131">Isso é feito acrescentando o caractere ao final do literal.</span><span class="sxs-lookup"><span data-stu-id="16af3-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="16af3-132">A tabela a seguir mostra os caracteres de tipo literal disponíveis com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="16af3-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="16af3-133">Caractere de tipo literal</span><span class="sxs-lookup"><span data-stu-id="16af3-133">Literal type character</span></span>|<span data-ttu-id="16af3-134">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="16af3-134">Data type</span></span>|<span data-ttu-id="16af3-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16af3-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="16af3-136">Nenhum caractere de tipo literal existe para o `Boolean`, `Byte`, `Date`, `Object`, `SByte`, ou `String` tipos de dados, ou para quaisquer tipos de dados compostos, como arrays ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="16af3-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="16af3-137">Literais também podem usar os caracteres de tipo identificador (`%`, `&`, `@`, `!`, `#`, `$`), como variáveis, constantes e expressões.</span><span class="sxs-lookup"><span data-stu-id="16af3-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="16af3-138">No entanto, o literal digitar caracteres (`S`, `I`, `L`, `D`, `F`, `R`, `C`) pode ser usado somente com literais.</span><span class="sxs-lookup"><span data-stu-id="16af3-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="16af3-139">Em todos os casos, o caractere de tipo literal deve seguir imediatamente o valor literal.</span><span class="sxs-lookup"><span data-stu-id="16af3-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="16af3-140">Literais hexadecimais, binários e octais</span><span class="sxs-lookup"><span data-stu-id="16af3-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="16af3-141">Normalmente, o compilador interpreta um literal inteiro para ser do sistema de número decimal (base 10).</span><span class="sxs-lookup"><span data-stu-id="16af3-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="16af3-142">Você também pode definir um literal inteiro como um número hexadecimal (base 16) com o `&H` prefixo, como um número binário (base 2) com o `&B` prefixo e como um octal (base 8) número com o `&O` prefixo.</span><span class="sxs-lookup"><span data-stu-id="16af3-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="16af3-143">Os dígitos após o prefixo devem ser apropriados para o sistema de número.</span><span class="sxs-lookup"><span data-stu-id="16af3-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="16af3-144">A tabela a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="16af3-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="16af3-145">Número base</span><span class="sxs-lookup"><span data-stu-id="16af3-145">Number base</span></span>|<span data-ttu-id="16af3-146">Prefixo</span><span class="sxs-lookup"><span data-stu-id="16af3-146">Prefix</span></span>|<span data-ttu-id="16af3-147">Valores de dígito válido</span><span class="sxs-lookup"><span data-stu-id="16af3-147">Valid digit values</span></span>|<span data-ttu-id="16af3-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16af3-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="16af3-149">Hexadecimal (base 16)</span><span class="sxs-lookup"><span data-stu-id="16af3-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="16af3-150">0-9 e A-F</span><span class="sxs-lookup"><span data-stu-id="16af3-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="16af3-151">Binário (base 2)</span><span class="sxs-lookup"><span data-stu-id="16af3-151">Binary (base 2)</span></span>|`0B`|<span data-ttu-id="16af3-152">0-1</span><span class="sxs-lookup"><span data-stu-id="16af3-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="16af3-153">Octal (base 8)</span><span class="sxs-lookup"><span data-stu-id="16af3-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="16af3-154">0-7</span><span class="sxs-lookup"><span data-stu-id="16af3-154">0-7</span></span>|`&O77`|

<span data-ttu-id="16af3-155">A partir de 2017 Visual Basic, você pode usar o caractere de sublinhado (`_`) como um separador de grupo para melhorar a legibilidade de um literal inteiro.</span><span class="sxs-lookup"><span data-stu-id="16af3-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="16af3-156">O exemplo a seguir usa o `_` caractere para agrupar um binário literal em grupos de 8 bits:</span><span class="sxs-lookup"><span data-stu-id="16af3-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="16af3-157">Você pode seguir um literal prefixado com um caractere de tipo literal.</span><span class="sxs-lookup"><span data-stu-id="16af3-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="16af3-158">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="16af3-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="16af3-159">No exemplo anterior, `counter` tem o valor decimal de -32768, e `flags` possui o valor decimal de + 32768.</span><span class="sxs-lookup"><span data-stu-id="16af3-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

## <a name="see-also"></a><span data-ttu-id="16af3-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16af3-160">See Also</span></span>

 [<span data-ttu-id="16af3-161">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="16af3-161">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="16af3-162">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="16af3-162">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="16af3-163">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="16af3-163">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="16af3-164">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="16af3-164">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="16af3-165">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="16af3-165">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="16af3-166">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="16af3-166">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="16af3-167">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="16af3-167">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
