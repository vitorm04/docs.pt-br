---
title: Widening (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825307"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="11761-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11761-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="11761-103">Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode conter todos os possíveis valores da classe ou estrutura original.</span><span class="sxs-lookup"><span data-stu-id="11761-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="11761-104">Convertendo com a palavra-chave Widening</span><span class="sxs-lookup"><span data-stu-id="11761-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="11761-105">O procedimento de conversão deve especificar `Public Shared` além `Widening`.</span><span class="sxs-lookup"><span data-stu-id="11761-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="11761-106">Conversões de ampliação sempre ter êxito em tempo de execução e nunca incorrerá em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="11761-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="11761-107">Os exemplos são `Single` à `Double`, `Char` para `String`e um tipo derivado para seu tipo base.</span><span class="sxs-lookup"><span data-stu-id="11761-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="11761-108">Essa última conversão está ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.</span><span class="sxs-lookup"><span data-stu-id="11761-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="11761-109">O código de consumo não precisa usar `CType` para conversões de ampliação, mesmo que `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="11761-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="11761-110">O `Widening` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="11761-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="11761-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="11761-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="11761-112">Por exemplo as definições de ampliação e redução de operadores de conversão, consulte [como: Definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="11761-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11761-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11761-113">See also</span></span>

- [<span data-ttu-id="11761-114">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="11761-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="11761-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="11761-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="11761-116">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="11761-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="11761-117">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="11761-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="11761-118">Função CType</span><span class="sxs-lookup"><span data-stu-id="11761-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="11761-119">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="11761-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="11761-120">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="11761-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
