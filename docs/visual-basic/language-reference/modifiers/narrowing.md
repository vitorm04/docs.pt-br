---
title: Narrowing
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
ms.openlocfilehash: f7724053e3732c909523e4e2d3b65bb1918c29d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362353"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="f2ca9-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2ca9-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="f2ca9-103">Indica que um operador de conversão ( `CType` ) converte uma classe ou estrutura em um tipo que pode não ser capaz de conter alguns dos valores possíveis da classe ou estrutura original.</span><span class="sxs-lookup"><span data-stu-id="f2ca9-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="f2ca9-104">Convertendo com a palavra-chave Narrowing</span><span class="sxs-lookup"><span data-stu-id="f2ca9-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="f2ca9-105">O procedimento de conversão deve especificar, `Public Shared` além de `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="f2ca9-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="f2ca9-106">As conversões redutoras nem sempre são bem sucedidas em tempo de execução e podem falhar ou incorrer em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="f2ca9-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="f2ca9-107">Os exemplos são `Long` to, `Integer` `String` to `Date` e um tipo base para um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="f2ca9-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="f2ca9-108">Essa última conversão é restrita porque o tipo base pode não conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="f2ca9-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="f2ca9-109">Se `Option Strict` for `On` , o código de consumo deve usar `CType` para todas as conversões redutoras.</span><span class="sxs-lookup"><span data-stu-id="f2ca9-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="f2ca9-110">A `Narrowing` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="f2ca9-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="f2ca9-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="f2ca9-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f2ca9-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="f2ca9-112">See also</span></span>

- [<span data-ttu-id="f2ca9-113">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="f2ca9-113">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="f2ca9-114">Widening</span><span class="sxs-lookup"><span data-stu-id="f2ca9-114">Widening</span></span>](widening.md)
- [<span data-ttu-id="f2ca9-115">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="f2ca9-115">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="f2ca9-116">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="f2ca9-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="f2ca9-117">Função CType</span><span class="sxs-lookup"><span data-stu-id="f2ca9-117">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="f2ca9-118">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="f2ca9-118">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
