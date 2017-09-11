---
title: Narrowing (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.narrowing
dev_langs:
- VB
helpviewer_keywords:
- conversions, type
- type conversion
- conversions, data type
- Narrowing keyword
- data type conversion
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 10
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
ms.openlocfilehash: 5cc086f122ef20573677513d9c6f79ee0873b837
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="a6370-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6370-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="a6370-103">Indica que um operador de conversão (`CType`) converte uma classe ou estrutura em um tipo que pode não ser capaz de armazenar alguns dos possíveis valores da classe ou estrutura original.</span><span class="sxs-lookup"><span data-stu-id="a6370-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="a6370-104">Convertendo com a palavra-chave Narrowing</span><span class="sxs-lookup"><span data-stu-id="a6370-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="a6370-105">O procedimento de conversão deve especificar `Public Shared` além `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="a6370-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="a6370-106">Conversões de estreitamento nem sempre bem-sucedidas em tempo de execução e podem falhar ou provoca perda de dados.</span><span class="sxs-lookup"><span data-stu-id="a6370-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="a6370-107">Os exemplos são `Long` para `Integer`, `String` para `Date`e um tipo base para um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="a6370-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="a6370-108">Esse último conversão é restritiva porque o tipo base pode não conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="a6370-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="a6370-109">Se `Option Strict` é `On`, o código de consumo deve usar `CType` para todas as conversões de redução.</span><span class="sxs-lookup"><span data-stu-id="a6370-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="a6370-110">O `Narrowing` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="a6370-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="a6370-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="a6370-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6370-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6370-112">See Also</span></span>  
 <span data-ttu-id="a6370-113">[Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a6370-113">[Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="a6370-114"> [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="a6370-114"> [Widening](../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="a6370-115"> [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="a6370-115"> [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="a6370-116"> [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="a6370-116"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="a6370-117"> [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md) </span><span class="sxs-lookup"><span data-stu-id="a6370-117"> [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) </span></span>  
<span data-ttu-id="a6370-118"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a6370-118"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
