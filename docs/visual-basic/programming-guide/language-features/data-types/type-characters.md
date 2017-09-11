---
title: Digite os caracteres (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
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
ms.openlocfilehash: 335306eca12070de456a72e918bcbba1e22ab55b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="1bee2-102">Caracteres de tipo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bee2-102">Type Characters (Visual Basic)</span></span>
<span data-ttu-id="1bee2-103">Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação com um *caractere de tipo*.</span><span class="sxs-lookup"><span data-stu-id="1bee2-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="1bee2-104">O caractere de tipo deve vir logo após o elemento, com nenhum caractere intermediário de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="1bee2-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>  
  
 <span data-ttu-id="1bee2-105">O caractere de tipo não é parte do nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="1bee2-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="1bee2-106">Um elemento definido com um caractere de tipo pode ser referenciado sem o caractere de tipo.</span><span class="sxs-lookup"><span data-stu-id="1bee2-106">An element defined with a type character can be referenced without the type character.</span></span>  
  
## <a name="identifier-type-characters"></a><span data-ttu-id="1bee2-107">Caracteres de tipo identificador</span><span class="sxs-lookup"><span data-stu-id="1bee2-107">Identifier Type Characters</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="1bee2-108">Fornece um conjunto de *caracteres de tipo identificador*, que você pode usar em uma declaração para especificar o tipo de dados de uma variável ou constante.</span><span class="sxs-lookup"><span data-stu-id="1bee2-108"> supplies a set of *identifier type characters*, which you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="1bee2-109">A tabela a seguir mostra os caracteres de tipo identificador disponíveis com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="1bee2-109">The following table shows the available identifier type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="1bee2-110">Caractere de tipo identificador</span><span class="sxs-lookup"><span data-stu-id="1bee2-110">Identifier type character</span></span>|<span data-ttu-id="1bee2-111">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="1bee2-111">Data type</span></span>|<span data-ttu-id="1bee2-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bee2-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="1bee2-113">Nenhum caractere de tipo identificador existe para o `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort` tipos de dados, ou para quaisquer tipos de dados compostos, como arrays ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="1bee2-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="1bee2-114">Em alguns casos, você pode acrescentar o `$` caracteres para um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] funcionar, por exemplo `Left$` em vez de `Left`, para obter um valor retornado do tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="1bee2-114">In some cases, you can append the `$` character to a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>  
  
 <span data-ttu-id="1bee2-115">Em todos os casos, o caractere de tipo identificador deve seguir imediatamente o nome do identificador.</span><span class="sxs-lookup"><span data-stu-id="1bee2-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>  
  
## <a name="literal-type-characters"></a><span data-ttu-id="1bee2-116">Caracteres de tipo literal</span><span class="sxs-lookup"><span data-stu-id="1bee2-116">Literal Type Characters</span></span>  
 <span data-ttu-id="1bee2-117">A *literal* é uma representação textual de um determinado valor de um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="1bee2-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  
  
### <a name="default-literal-types"></a><span data-ttu-id="1bee2-118">Tipos de Literal padrão</span><span class="sxs-lookup"><span data-stu-id="1bee2-118">Default Literal Types</span></span>  
 <span data-ttu-id="1bee2-119">A forma de um literal como ele aparece no seu código normalmente determina seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="1bee2-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="1bee2-120">A tabela a seguir mostra esses tipos padrão.</span><span class="sxs-lookup"><span data-stu-id="1bee2-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="1bee2-121">Formato textual de literal</span><span class="sxs-lookup"><span data-stu-id="1bee2-121">Textual form of literal</span></span>|<span data-ttu-id="1bee2-122">Tipo de dados padrão</span><span class="sxs-lookup"><span data-stu-id="1bee2-122">Default data type</span></span>|<span data-ttu-id="1bee2-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bee2-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="1bee2-124">Numérico, sem parte fracionária</span><span class="sxs-lookup"><span data-stu-id="1bee2-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="1bee2-125">Numérico, sem parte fracionária, muito grande para`Integer`</span><span class="sxs-lookup"><span data-stu-id="1bee2-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="1bee2-126">Numérico, parte fracionária</span><span class="sxs-lookup"><span data-stu-id="1bee2-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="1bee2-127">Entre aspas duplas</span><span class="sxs-lookup"><span data-stu-id="1bee2-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="1bee2-128">Entre sinais numéricos</span><span class="sxs-lookup"><span data-stu-id="1bee2-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a><span data-ttu-id="1bee2-129">Tipos literais forçados</span><span class="sxs-lookup"><span data-stu-id="1bee2-129">Forced Literal Types</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="1bee2-130">Fornece um conjunto de *caracteres de tipo literal*, indicando que você pode usar para forçar um literal a assumir um tipo de dados que não seja o seu formulário.</span><span class="sxs-lookup"><span data-stu-id="1bee2-130"> supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="1bee2-131">Para fazer isso, acrescentando o caractere ao final do literal.</span><span class="sxs-lookup"><span data-stu-id="1bee2-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="1bee2-132">A tabela a seguir mostra os caracteres de tipo literal disponíveis com exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="1bee2-132">The following table shows the available literal type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="1bee2-133">Caractere de tipo literal</span><span class="sxs-lookup"><span data-stu-id="1bee2-133">Literal type character</span></span>|<span data-ttu-id="1bee2-134">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="1bee2-134">Data type</span></span>|<span data-ttu-id="1bee2-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bee2-135">Example</span></span>|  
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
  
 <span data-ttu-id="1bee2-136">Nenhum caractere de tipo literal existe para o `Boolean`, `Byte`, `Date`, `Object`, `SByte`, ou `String` tipos de dados, ou para quaisquer tipos de dados compostos, como arrays ou estruturas.</span><span class="sxs-lookup"><span data-stu-id="1bee2-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="1bee2-137">Literais também podem usar os caracteres de tipo identificador (`%`, `&`, `@`, `!`, `#`, `$`), como variáveis, constantes e expressões.</span><span class="sxs-lookup"><span data-stu-id="1bee2-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="1bee2-138">No entanto, o literal digitar caracteres (`S`, `I`, `L`, `D`, `F`, `R`, `C`) pode ser usado somente com literais.</span><span class="sxs-lookup"><span data-stu-id="1bee2-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>  
  
 <span data-ttu-id="1bee2-139">Em todos os casos, o caractere de tipo literal deve vir logo após o valor literal.</span><span class="sxs-lookup"><span data-stu-id="1bee2-139">In all cases, the literal type character must immediately follow the literal value.</span></span>  
  
## <a name="hexadecimal-and-octal-literals"></a><span data-ttu-id="1bee2-140">Literais octais e hexadecimais</span><span class="sxs-lookup"><span data-stu-id="1bee2-140">Hexadecimal and Octal Literals</span></span>  
 <span data-ttu-id="1bee2-141">O compilador normalmente constrói um literal inteiro para ser do sistema de número decimal (base 10).</span><span class="sxs-lookup"><span data-stu-id="1bee2-141">The compiler normally construes an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="1bee2-142">Você pode forçar um literal inteiro para ser hexadecimal (base 16) com o `&H` prefixo e você pode forçá-lo para ser octal (base 8) com o `&O` prefixo.</span><span class="sxs-lookup"><span data-stu-id="1bee2-142">You can force an integer literal to be hexadecimal (base 16) with the `&H` prefix, and you can force it to be octal (base 8) with the `&O` prefix.</span></span> <span data-ttu-id="1bee2-143">Os dígitos que seguem o prefixo devem ser apropriados para o sistema numérico.</span><span class="sxs-lookup"><span data-stu-id="1bee2-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="1bee2-144">A tabela a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="1bee2-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="1bee2-145">Número base</span><span class="sxs-lookup"><span data-stu-id="1bee2-145">Number base</span></span>|<span data-ttu-id="1bee2-146">Prefixo</span><span class="sxs-lookup"><span data-stu-id="1bee2-146">Prefix</span></span>|<span data-ttu-id="1bee2-147">Valores válidos de dígitos</span><span class="sxs-lookup"><span data-stu-id="1bee2-147">Valid digit values</span></span>|<span data-ttu-id="1bee2-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bee2-148">Example</span></span>|  
|-----------------|------------|------------------------|-------------|  
|<span data-ttu-id="1bee2-149">Hexadecimal (base 16)</span><span class="sxs-lookup"><span data-stu-id="1bee2-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="1bee2-150">0-9 e A-F</span><span class="sxs-lookup"><span data-stu-id="1bee2-150">0-9 and A-F</span></span>|`&HFFFF`|  
|<span data-ttu-id="1bee2-151">Octal (base 8)</span><span class="sxs-lookup"><span data-stu-id="1bee2-151">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="1bee2-152">0-7</span><span class="sxs-lookup"><span data-stu-id="1bee2-152">0-7</span></span>|`&O77`|  
  
 <span data-ttu-id="1bee2-153">Você pode seguir um literal prefixado com um caractere de tipo literal.</span><span class="sxs-lookup"><span data-stu-id="1bee2-153">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="1bee2-154">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="1bee2-154">The following example shows this.</span></span>  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 <span data-ttu-id="1bee2-155">No exemplo anterior, `counter` tem o valor decimal de -32768, e `flags` possui o valor decimal de +&32768;.</span><span class="sxs-lookup"><span data-stu-id="1bee2-155">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bee2-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bee2-156">See Also</span></span>  
 <span data-ttu-id="1bee2-157">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="1bee2-157">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="1bee2-158"> [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1bee2-158"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="1bee2-159"> [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="1bee2-159"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="1bee2-160"> [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="1bee2-160"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="1bee2-161"> [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="1bee2-161"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="1bee2-162"> [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="1bee2-162"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="1bee2-163"> [Tipos de Dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span><span class="sxs-lookup"><span data-stu-id="1bee2-163"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span></span>
