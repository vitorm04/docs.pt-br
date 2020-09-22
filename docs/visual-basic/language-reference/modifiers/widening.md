---
title: Widening
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
ms.openlocfilehash: 14e0b026f4fc3b0bf202ea643a28d6f1a7df2b7c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867643"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="cd07c-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd07c-102">Widening (Visual Basic)</span></span>

<span data-ttu-id="cd07c-103">Indica que um operador de conversão ( `CType` ) converte uma classe ou estrutura em um tipo que pode conter todos os valores possíveis da classe ou estrutura original.</span><span class="sxs-lookup"><span data-stu-id="cd07c-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="cd07c-104">Convertendo com a palavra-chave Widening</span><span class="sxs-lookup"><span data-stu-id="cd07c-104">Converting with the Widening Keyword</span></span>  

 <span data-ttu-id="cd07c-105">O procedimento de conversão deve especificar, `Public Shared` além de `Widening` .</span><span class="sxs-lookup"><span data-stu-id="cd07c-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="cd07c-106">Conversões de alargamento sempre são bem sucedidos em tempo de execução e nunca incorrem em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="cd07c-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="cd07c-107">Os exemplos são `Single` to, `Double` `Char` to `String` e um tipo derivado para seu tipo base.</span><span class="sxs-lookup"><span data-stu-id="cd07c-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="cd07c-108">Essa última conversão está se ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.</span><span class="sxs-lookup"><span data-stu-id="cd07c-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="cd07c-109">O código de consumo não precisa usar o `CType` para conversões de ampliação, mesmo se `Option Strict` for `On` .</span><span class="sxs-lookup"><span data-stu-id="cd07c-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="cd07c-110">A `Widening` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="cd07c-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="cd07c-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="cd07c-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="cd07c-112">Para obter exemplos de definições de ampliação e limitação de operadores de conversão, consulte [como definir um operador de conversão](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="cd07c-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd07c-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="cd07c-113">See also</span></span>

- [<span data-ttu-id="cd07c-114">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="cd07c-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="cd07c-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="cd07c-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="cd07c-116">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="cd07c-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="cd07c-117">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="cd07c-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="cd07c-118">Função CType</span><span class="sxs-lookup"><span data-stu-id="cd07c-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="cd07c-119">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="cd07c-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="cd07c-120">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="cd07c-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
