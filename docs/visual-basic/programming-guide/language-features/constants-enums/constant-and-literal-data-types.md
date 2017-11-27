---
title: Tipos de dados constante e literal (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554753e26d185593ce43b741b3b2f9e3cb1ad6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="constant-and-literal-data-types-visual-basic"></a><span data-ttu-id="25086-102">Tipos de dados constante e literal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25086-102">Constant and Literal Data Types (Visual Basic)</span></span>
<span data-ttu-id="25086-103">Um literal é um valor que é expresso como si mesmo em vez de um valor variável ou o resultado de uma expressão, como o número 3 ou a cadeia de caracteres "Olá".</span><span class="sxs-lookup"><span data-stu-id="25086-103">A literal is a value that is expressed as itself rather than as a variable's value or the result of an expression, such as the number 3 or the string "Hello".</span></span> <span data-ttu-id="25086-104">Uma constante é um nome significativo que toma o lugar de um literal e mantém esse mesmo valor em todo o programa, em vez de uma variável, cujo valor pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="25086-104">A constant is a meaningful name that takes the place of a literal and retains this same value throughout the program, as opposed to a variable, whose value may change.</span></span>  
  
 <span data-ttu-id="25086-105">Quando [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) é `Off` e [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) é `On`, você deve declarar todas as constantes explicitamente com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="25086-105">When [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) is `Off` and [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) is `On`, you must declare all constants explicitly with a data type.</span></span> <span data-ttu-id="25086-106">No exemplo a seguir, o tipo de dados `MyByte` é declarado explicitamente como tipo de dados `Byte`:</span><span class="sxs-lookup"><span data-stu-id="25086-106">In the following example, the data type of `MyByte` is explicitly declared as data type `Byte`:</span></span>  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 <span data-ttu-id="25086-107">Quando `Option Infer` é `On` ou `Option Strict` é `Off`, você pode declarar uma constante sem especificar um tipo de dados com um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="25086-107">When `Option Infer` is `On` or `Option Strict` is `Off`, you can declare a constant without specifying a data type with an `As` clause.</span></span> <span data-ttu-id="25086-108">O compilador determina o tipo de constante do tipo da expressão.</span><span class="sxs-lookup"><span data-stu-id="25086-108">The compiler determines the type of the constant from the type of the expression.</span></span> <span data-ttu-id="25086-109">Um literal de inteiro numérica é convertido por padrão para o `Integer` tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="25086-109">A numeric integer literal is cast by default to the `Integer` data type.</span></span> <span data-ttu-id="25086-110">Tipo de dados padrão para números de ponto flutuante são `Double`e as palavras-chave `True` e `False` especificar um `Boolean` constante.</span><span class="sxs-lookup"><span data-stu-id="25086-110">The default data type for floating-point numbers is `Double`, and the keywords `True` and `False` specify a `Boolean` constant.</span></span>  
  
## <a name="literals-and-type-coercion"></a><span data-ttu-id="25086-111">Literais e coerção de tipo</span><span class="sxs-lookup"><span data-stu-id="25086-111">Literals and Type Coercion</span></span>  
 <span data-ttu-id="25086-112">Em alguns casos, talvez você queira forçar um literal para um determinado tipo de dados; Por exemplo, ao atribuir um valor literal inteiro muito grande a uma variável do tipo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="25086-112">In some cases, you might want to force a literal to a particular data type; for example, when assigning a particularly large integral literal value to a variable of type `Decimal`.</span></span> <span data-ttu-id="25086-113">O exemplo a seguir produz um erro:</span><span class="sxs-lookup"><span data-stu-id="25086-113">The following example produces an error:</span></span>  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 <span data-ttu-id="25086-114">Os resultados de erro da representação do literal.</span><span class="sxs-lookup"><span data-stu-id="25086-114">The error results from the representation of the literal.</span></span> <span data-ttu-id="25086-115">O `Decimal` tipo de dados pode conter um valor muito grande, mas o literal implicitamente é representado como um `Long`, que não é possível.</span><span class="sxs-lookup"><span data-stu-id="25086-115">The `Decimal` data type can hold a value this large, but the literal is implicitly represented as a `Long`, which cannot.</span></span>  
  
 <span data-ttu-id="25086-116">Você pode forçar um literal para um determinado tipo de dados de duas maneiras: anexando um caractere de tipo a ele ou colocando-o entre caracteres delimitadores.</span><span class="sxs-lookup"><span data-stu-id="25086-116">You can coerce a literal to a particular data type in two ways: by appending a type character to it, or by placing it within enclosing characters.</span></span> <span data-ttu-id="25086-117">Um caractere de tipo ou delimitador caracteres deve imediatamente preceder e/ou execute o literal, sem nenhum espaço intermediárias ou caracteres de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="25086-117">A type character or enclosing characters must immediately precede and/or follow the literal, with no intervening space or characters of any kind.</span></span>  
  
 <span data-ttu-id="25086-118">Para fazer com que o exemplo anterior funcionar, você pode acrescentar o `D` digite o caractere literal, o que faz com que ele seja representado como um `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="25086-118">To make the previous example work, you can append the `D` type character to the literal, which causes it to be represented as a `Decimal`:</span></span>  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 <span data-ttu-id="25086-119">O exemplo a seguir demonstra o uso correto dos caracteres de tipo e delimitador:</span><span class="sxs-lookup"><span data-stu-id="25086-119">The following example demonstrates correct usage of type characters and enclosing characters:</span></span>  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 <span data-ttu-id="25086-120">A tabela a seguir mostra os caracteres delimitadores e tipos de caracteres disponíveis no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25086-120">The following table shows the enclosing characters and type characters available in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
|<span data-ttu-id="25086-121">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="25086-121">Data type</span></span>|<span data-ttu-id="25086-122">Caractere delimitador</span><span class="sxs-lookup"><span data-stu-id="25086-122">Enclosing character</span></span>|<span data-ttu-id="25086-123">Caractere de tipo acrescentado</span><span class="sxs-lookup"><span data-stu-id="25086-123">Appended type character</span></span>|  
|---|---|---|  
|`Boolean`|<span data-ttu-id="25086-124">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-124">(none)</span></span>|<span data-ttu-id="25086-125">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-125">(none)</span></span>|  
|`Byte`|<span data-ttu-id="25086-126">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-126">(none)</span></span>|<span data-ttu-id="25086-127">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-127">(none)</span></span>|  
|`Char`|<span data-ttu-id="25086-128">"</span><span class="sxs-lookup"><span data-stu-id="25086-128">"</span></span>|<span data-ttu-id="25086-129">C</span><span class="sxs-lookup"><span data-stu-id="25086-129">C</span></span>|  
|`Date`|#|<span data-ttu-id="25086-130">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-130">(none)</span></span>|  
|`Decimal`|<span data-ttu-id="25086-131">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-131">(none)</span></span>|<span data-ttu-id="25086-132">D ou @</span><span class="sxs-lookup"><span data-stu-id="25086-132">D or @</span></span>|  
|`Double`|<span data-ttu-id="25086-133">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-133">(none)</span></span>|<span data-ttu-id="25086-134">R ou #</span><span class="sxs-lookup"><span data-stu-id="25086-134">R or #</span></span>|  
|`Integer`|<span data-ttu-id="25086-135">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-135">(none)</span></span>|<span data-ttu-id="25086-136">I ou %</span><span class="sxs-lookup"><span data-stu-id="25086-136">I or %</span></span>|  
|`Long`|<span data-ttu-id="25086-137">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-137">(none)</span></span>|<span data-ttu-id="25086-138">L ou &</span><span class="sxs-lookup"><span data-stu-id="25086-138">L or &</span></span>|  
|`Short`|<span data-ttu-id="25086-139">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-139">(none)</span></span>|<span data-ttu-id="25086-140">S</span><span class="sxs-lookup"><span data-stu-id="25086-140">S</span></span>|  
|`Single`|<span data-ttu-id="25086-141">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-141">(none)</span></span>|<span data-ttu-id="25086-142">F ou!</span><span class="sxs-lookup"><span data-stu-id="25086-142">F or !</span></span>|  
|`String`|<span data-ttu-id="25086-143">"</span><span class="sxs-lookup"><span data-stu-id="25086-143">"</span></span>|<span data-ttu-id="25086-144">(nenhum)</span><span class="sxs-lookup"><span data-stu-id="25086-144">(none)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25086-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25086-145">See Also</span></span>  
 [<span data-ttu-id="25086-146">Constantes Definidas pelo Usuário</span><span class="sxs-lookup"><span data-stu-id="25086-146">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="25086-147">Como declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="25086-147">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="25086-148">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="25086-148">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="25086-149">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="25086-149">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="25086-150">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="25086-150">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="25086-151">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="25086-151">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="25086-152">Como: declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="25086-152">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="25086-153">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="25086-153">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="25086-154">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="25086-154">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="25086-155">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="25086-155">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
