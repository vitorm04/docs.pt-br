---
title: Operador *=
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 4e2f18fb2b8110d97390390b3934d3c1761baa35
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866741"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e45ce-102">Operador \*= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e45ce-102">\*= Operator (Visual Basic)</span></span>

<span data-ttu-id="e45ce-103">Multiplica o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="e45ce-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e45ce-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e45ce-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e45ce-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="e45ce-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e45ce-106">Required.</span></span> <span data-ttu-id="e45ce-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="e45ce-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e45ce-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="e45ce-108">Required.</span></span> <span data-ttu-id="e45ce-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="e45ce-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e45ce-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e45ce-110">Remarks</span></span>  

 <span data-ttu-id="e45ce-111">O elemento no lado esquerdo do `*=` operador pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="e45ce-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e45ce-112">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="e45ce-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e45ce-113">`*=`Primeiro, o operador multiplica o valor da expressão (no lado direito do operador) pelo valor da variável ou da propriedade (no lado esquerdo do operador), em seguida.</span><span class="sxs-lookup"><span data-stu-id="e45ce-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="e45ce-114">Em seguida, o operador atribui o resultado dessa operação à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="e45ce-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e45ce-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="e45ce-115">Overloading</span></span>  

 <span data-ttu-id="e45ce-116">O [operador \*](multiplication-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e45ce-116">The [\* Operator](multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e45ce-117">Sobrecarregar o `*` operador afeta o comportamento do `*=` operador.</span><span class="sxs-lookup"><span data-stu-id="e45ce-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="e45ce-118">Se o seu código usa `*=` em uma classe ou estrutura que sobrecarrega, certifique-se de `*` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="e45ce-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e45ce-119">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e45ce-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e45ce-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e45ce-120">Example</span></span>  

 <span data-ttu-id="e45ce-121">O exemplo a seguir usa o `*=` operador para multiplicar uma `Integer` variável por um segundo e atribuir o resultado à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="e45ce-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e45ce-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="e45ce-122">See also</span></span>

- [<span data-ttu-id="e45ce-123">\* Operador</span><span class="sxs-lookup"><span data-stu-id="e45ce-123">\* Operator</span></span>](multiplication-operator.md)
- [<span data-ttu-id="e45ce-124">Operadores de atribuição</span><span class="sxs-lookup"><span data-stu-id="e45ce-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="e45ce-125">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="e45ce-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="e45ce-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e45ce-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="e45ce-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="e45ce-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="e45ce-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="e45ce-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
