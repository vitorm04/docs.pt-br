---
title: Tipos de dados constante e Literal (Visual Basic) | Documentos do Microsoft
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
- declaring constants, literal data types
- data types [Visual Basic], declaring
- constants, declaring
- explicit declarations
- literals, coercing data type
- declarations, data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
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
ms.openlocfilehash: 29a997ee0dd847e8505d1a5c24cacfdfdb0a42cc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="07ab2-102">Tipos de dados constante e literal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07ab2-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="07ab2-103">Um literal é um valor que é expresso como si mesmo em vez de um valor de variável ou o resultado de uma expressão, como o número 3 ou a cadeia de caracteres "Hello".</span><span class="sxs-lookup"><span data-stu-id="07ab2-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="07ab2-104">Uma constante é um nome significativo que toma o lugar de um literal e mantém esse mesmo valor em todo o programa, em vez de uma variável, cujo valor pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="07ab2-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="07ab2-105">Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar todas as constantes explicitamente com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="07ab2-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="07ab2-106">No exemplo a seguir, o tipo de dados `MyByte` for declarado explicitamente como tipo de dados `Byte`:</span><span class="sxs-lookup"><span data-stu-id="07ab2-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 <span data-ttu-id="07ab2-107">[!code-vb[VbVbalrConstants n º&1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="07ab2-107">[!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="07ab2-108">Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="07ab2-108">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="07ab2-109">O compilador determina o tipo da constante do tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="07ab2-109">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="07ab2-110">Um literal numérico de inteiro é convertido por padrão para o `Integer` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="07ab2-110">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="07ab2-111">Tipo de dados padrão para números de ponto flutuante são `Double`e as palavras-chave `True` e `False` especificar um `Boolean` constante.</span><span class="sxs-lookup"><span data-stu-id="07ab2-111">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="07ab2-112">Literais e coerção de tipo</span><span class="sxs-lookup"><span data-stu-id="07ab2-112">Literals and Type Coercion</span></span>  
 <span data-ttu-id="07ab2-113">Em alguns casos, talvez você queira forçar um literal para um determinado tipo de dados; Por exemplo, ao atribuir um valor literal inteiro muito grande a uma variável do tipo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="07ab2-113">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="07ab2-114">O exemplo a seguir produz um erro:</span><span class="sxs-lookup"><span data-stu-id="07ab2-114">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="07ab2-115">O erro resulta da representação da literal.</span><span class="sxs-lookup"><span data-stu-id="07ab2-115">The error results from the representation of the literal.</span></span> <span data-ttu-id="07ab2-116">O `Decimal` tipo de dados pode conter um valor muito grande, mas o literal implicitamente é representado como um `Long`, que não é possível.</span><span class="sxs-lookup"><span data-stu-id="07ab2-116">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="07ab2-117">Você pode forçar um literal para um determinado tipo de dados de duas maneiras: anexando um caractere de tipo a ele ou o colocando entre caracteres delimitadores.</span><span class="sxs-lookup"><span data-stu-id="07ab2-117">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="07ab2-118">Um caractere de tipo ou delimitador caracteres deve imediatamente preceder e/ou suceder o literal, sem nenhum espaço intermediárias ou caracteres de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="07ab2-118">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="07ab2-119">Para que o exemplo anterior funcione, você pode acrescentar o `D` digite o caractere literal, o que faz com que ele seja representado como um `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="07ab2-119">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 <span data-ttu-id="07ab2-120">[!code-vb[VbVbalrConstants n º&2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="07ab2-120">[!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="07ab2-121">O exemplo a seguir demonstra o uso correto dos caracteres delimitadores e caracteres de tipo:</span><span class="sxs-lookup"><span data-stu-id="07ab2-121">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 <span data-ttu-id="07ab2-122">[!code-vb[VbVbalrConstants n º&3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="07ab2-122">[!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]</span></span>  
  
 <span data-ttu-id="07ab2-123">A tabela a seguir mostra os caracteres delimitadores e tipos de caracteres disponíveis no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="07ab2-123">The following table shows the enclosing characters and type characters available in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
|<span data-ttu-id="07ab2-124">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="07ab2-124">Data type</span></span>|<span data-ttu-id="07ab2-125">Caractere delimitador</span><span class="sxs-lookup"><span data-stu-id="07ab2-125">Enclosing character</span></span>|<span data-ttu-id="07ab2-126">Caractere de tipo acrescentado</span><span class="sxs-lookup"><span data-stu-id="07ab2-126">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="07ab2-127">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-127">(none)</span></span>|<span data-ttu-id="07ab2-128">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-128">(none)</span></span>|  
|`Byte`|<span data-ttu-id="07ab2-129">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-129">(none)</span></span>|<span data-ttu-id="07ab2-130">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-130">(none)</span></span>|  
|`Char`|<span data-ttu-id="07ab2-131">"</span><span class="sxs-lookup"><span data-stu-id="07ab2-131">"</span></span>|<span data-ttu-id="07ab2-132">C</span><span class="sxs-lookup"><span data-stu-id="07ab2-132">C</span></span>|  
|`Date`|#|<span data-ttu-id="07ab2-133">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-133">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="07ab2-134">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-134">(none)</span></span>|<span data-ttu-id="07ab2-135">D ou @</span><span class="sxs-lookup"><span data-stu-id="07ab2-135">D or @</span></span>|  
|`Double`|<span data-ttu-id="07ab2-136">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-136">(none)</span></span>|<span data-ttu-id="07ab2-137">R ou</span><span class="sxs-lookup"><span data-stu-id="07ab2-137">R or</span></span> #|  
|`Integer`|<span data-ttu-id="07ab2-138">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-138">(none)</span></span>|<span data-ttu-id="07ab2-139">Eu ou %</span><span class="sxs-lookup"><span data-stu-id="07ab2-139">I or %</span></span>|  
|`Long`|<span data-ttu-id="07ab2-140">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-140">(none)</span></span>|<span data-ttu-id="07ab2-141">L ou < /</span><span class="sxs-lookup"><span data-stu-id="07ab2-141">L or &</span></span>|  
|`Short`|<span data-ttu-id="07ab2-142">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-142">(none)</span></span>|<span data-ttu-id="07ab2-143">S</span><span class="sxs-lookup"><span data-stu-id="07ab2-143">S</span></span>|  
|`Single`|<span data-ttu-id="07ab2-144">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-144">(none)</span></span>|<span data-ttu-id="07ab2-145">F ou!</span><span class="sxs-lookup"><span data-stu-id="07ab2-145">F or !</span></span>|  
|`String`|<span data-ttu-id="07ab2-146">"</span><span class="sxs-lookup"><span data-stu-id="07ab2-146">"</span></span>|<span data-ttu-id="07ab2-147">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="07ab2-147">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07ab2-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07ab2-148">See Also</span></span>  
 <span data-ttu-id="07ab2-149">[Constantes definidas pelo usuário](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-149">[User-Defined Constants](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md) </span></span>  
<span data-ttu-id="07ab2-150"> [Como: declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-150"> [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md) </span></span>  
<span data-ttu-id="07ab2-151"> [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-151"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="07ab2-152"> [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-152"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="07ab2-153"> [Instrução Option Explicit](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-153"> [Option Explicit Statement](../../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="07ab2-154"> [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-154"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="07ab2-155"> [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-155"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="07ab2-156"> [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-156"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="07ab2-157"> [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="07ab2-157"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="07ab2-158"> [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="07ab2-158"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
