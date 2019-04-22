---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838840"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="523e2-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="523e2-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="523e2-103">Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode não ser capaz de manter alguns dos possíveis valores da classe ou estrutura original.</span><span class="sxs-lookup"><span data-stu-id="523e2-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="523e2-104">Convertendo com a palavra-chave Narrowing</span><span class="sxs-lookup"><span data-stu-id="523e2-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="523e2-105">O procedimento de conversão deve especificar `Public Shared` além `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="523e2-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="523e2-106">Conversões de estreitamento nem sempre ter êxito em tempo de execução e pode falhar ou causar a perda de dados.</span><span class="sxs-lookup"><span data-stu-id="523e2-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="523e2-107">Os exemplos são `Long` à `Integer`, `String` para `Date`e um tipo base para um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="523e2-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="523e2-108">Essa última conversão é restritiva porque o tipo base não pode conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="523e2-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="523e2-109">Se `Option Strict` está `On`, o código de consumo deve usar `CType` para todas as conversões de estreitamento.</span><span class="sxs-lookup"><span data-stu-id="523e2-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="523e2-110">O `Narrowing` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="523e2-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="523e2-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="523e2-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="523e2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="523e2-112">See also</span></span>

- [<span data-ttu-id="523e2-113">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="523e2-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="523e2-114">Ampliação</span><span class="sxs-lookup"><span data-stu-id="523e2-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="523e2-115">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="523e2-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="523e2-116">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="523e2-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="523e2-117">Função CType</span><span class="sxs-lookup"><span data-stu-id="523e2-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
- [<span data-ttu-id="523e2-118">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="523e2-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
