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
ms.openlocfilehash: 77515357ac9dc972992df09c471695aad13985c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867928"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="8ebaa-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ebaa-102">Narrowing (Visual Basic)</span></span>

<span data-ttu-id="8ebaa-103">Indica que um operador de conversão ( `CType` ) converte uma classe ou estrutura em um tipo que pode não ser capaz de conter alguns dos valores possíveis da classe ou estrutura original.</span><span class="sxs-lookup"><span data-stu-id="8ebaa-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="8ebaa-104">Convertendo com a palavra-chave Narrowing</span><span class="sxs-lookup"><span data-stu-id="8ebaa-104">Converting with the Narrowing Keyword</span></span>  

 <span data-ttu-id="8ebaa-105">O procedimento de conversão deve especificar, `Public Shared` além de `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="8ebaa-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="8ebaa-106">As conversões redutoras nem sempre são bem sucedidas em tempo de execução e podem falhar ou incorrer em perda de dados.</span><span class="sxs-lookup"><span data-stu-id="8ebaa-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="8ebaa-107">Os exemplos são `Long` to, `Integer` `String` to `Date` e um tipo base para um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="8ebaa-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="8ebaa-108">Essa última conversão é restrita porque o tipo base pode não conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="8ebaa-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="8ebaa-109">Se `Option Strict` for `On` , o código de consumo deve usar `CType` para todas as conversões redutoras.</span><span class="sxs-lookup"><span data-stu-id="8ebaa-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="8ebaa-110">A `Narrowing` palavra-chave pode ser usada neste contexto:</span><span class="sxs-lookup"><span data-stu-id="8ebaa-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="8ebaa-111">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="8ebaa-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ebaa-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ebaa-112">See also</span></span>

- [<span data-ttu-id="8ebaa-113">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="8ebaa-113">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="8ebaa-114">Widening</span><span class="sxs-lookup"><span data-stu-id="8ebaa-114">Widening</span></span>](widening.md)
- [<span data-ttu-id="8ebaa-115">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="8ebaa-115">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="8ebaa-116">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="8ebaa-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="8ebaa-117">Função CType</span><span class="sxs-lookup"><span data-stu-id="8ebaa-117">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="8ebaa-118">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="8ebaa-118">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
