---
title: "Expansão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.widening
dev_langs:
- VB
helpviewer_keywords:
- conversions, type
- type conversion
- conversions, data type
- Widening keyword
- data type conversion
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 616701c92e366f15b19dc1b67de888944b71f3e8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="widening-visual-basic"></a><span data-ttu-id="c3e55-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3e55-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="c3e55-103">Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode conter todos os possíveis valores da classe ou estrutura original.</span><span class="sxs-lookup"><span data-stu-id="c3e55-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="c3e55-104">Convertendo com a palavra-chave Widening</span><span class="sxs-lookup"><span data-stu-id="c3e55-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="c3e55-105">O procedimento de conversão deve especificar `Public Shared` além `Widening`.</span><span class="sxs-lookup"><span data-stu-id="c3e55-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="c3e55-106">Conversões de ampliação sempre são bem-sucedidas em tempo de execução e nunca provocam perda de dados.</span><span class="sxs-lookup"><span data-stu-id="c3e55-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="c3e55-107">Os exemplos são `Single` para `Double`, `Char` para `String`e um tipo derivado para seu tipo base.</span><span class="sxs-lookup"><span data-stu-id="c3e55-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="c3e55-108">Essa última conversão está ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.</span><span class="sxs-lookup"><span data-stu-id="c3e55-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="c3e55-109">O código consumidor não precisa usar `CType` para ampliação conversões, mesmo se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="c3e55-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="c3e55-110">O `Widening` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="c3e55-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="c3e55-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="c3e55-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="c3e55-112">Por exemplo, definições de widening e narrowing operadores de conversão, consulte [como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c3e55-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e55-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3e55-113">See Also</span></span>  
 <span data-ttu-id="c3e55-114">[Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c3e55-114">[Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="c3e55-115"> [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="c3e55-115"> [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="c3e55-116"> [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="c3e55-116"> [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="c3e55-117"> [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="c3e55-117"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="c3e55-118"> [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md) </span><span class="sxs-lookup"><span data-stu-id="c3e55-118"> [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) </span></span>  
<span data-ttu-id="c3e55-119"> [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c3e55-119"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="c3e55-120"> [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)</span><span class="sxs-lookup"><span data-stu-id="c3e55-120"> [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)</span></span>
