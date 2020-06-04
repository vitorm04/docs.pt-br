---
title: Operador \=
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: a546d8b0c9b3852386970f80d3da96794da2351c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370941"
---
# <a name="-operator"></a><span data-ttu-id="d91db-102">\\= Operador</span><span class="sxs-lookup"><span data-stu-id="d91db-102">\\= Operator</span></span>
<span data-ttu-id="d91db-103">Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado inteiro à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="d91db-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d91db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d91db-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d91db-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d91db-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d91db-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="d91db-106">Required.</span></span> <span data-ttu-id="d91db-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="d91db-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="d91db-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="d91db-108">Required.</span></span> <span data-ttu-id="d91db-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="d91db-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d91db-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d91db-110">Remarks</span></span>  
 <span data-ttu-id="d91db-111">O elemento no lado esquerdo do `\=` operador pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="d91db-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d91db-112">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="d91db-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d91db-113">O `\=` operador divide o valor de uma variável ou propriedade à esquerda pelo valor à direita e atribui o resultado inteiro à variável ou à propriedade à sua esquerda</span><span class="sxs-lookup"><span data-stu-id="d91db-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="d91db-114">Para obter mais informações sobre divisão de inteiros, consulte [\ Operator (Visual Basic)](integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d91db-114">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d91db-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="d91db-115">Overloading</span></span>  
 <span data-ttu-id="d91db-116">O `\` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="d91db-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d91db-117">Sobrecarregar o `\` operador afeta o comportamento do `\=` operador.</span><span class="sxs-lookup"><span data-stu-id="d91db-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="d91db-118">Se o seu código usa `\=` em uma classe ou estrutura que sobrecarrega, certifique-se de `\` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="d91db-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d91db-119">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d91db-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d91db-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d91db-120">Example</span></span>  
 <span data-ttu-id="d91db-121">O exemplo a seguir usa o `\=` operador para dividir uma `Integer` variável por um segundo e atribuir o resultado inteiro à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="d91db-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="d91db-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="d91db-122">See also</span></span>

- [<span data-ttu-id="d91db-123">Operador \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91db-123">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="d91db-124">Operador/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d91db-124">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="d91db-125">Operadores de atribuição</span><span class="sxs-lookup"><span data-stu-id="d91db-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="d91db-126">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="d91db-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="d91db-127">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d91db-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="d91db-128">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="d91db-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="d91db-129">Instruções</span><span class="sxs-lookup"><span data-stu-id="d91db-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
