---
title: '&amp;= Operador'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: db42f7be7225b866eacf5b73066754e91cd1a0f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371980"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="71058-102">&amp;= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71058-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="71058-103">Concatena uma `String` expressão a uma `String` variável ou propriedade e atribui o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="71058-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71058-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71058-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="71058-105">Partes</span><span class="sxs-lookup"><span data-stu-id="71058-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="71058-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="71058-106">Required.</span></span> <span data-ttu-id="71058-107">Qualquer `String` variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="71058-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="71058-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="71058-108">Required.</span></span> <span data-ttu-id="71058-109">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="71058-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71058-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="71058-110">Remarks</span></span>  
 <span data-ttu-id="71058-111">O elemento no lado esquerdo do `&=` operador pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="71058-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="71058-112">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="71058-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="71058-113">O `&=` operador concatena a `String` expressão à direita para a `String` variável ou propriedade à esquerda e atribui o resultado à variável ou à propriedade à esquerda.</span><span class="sxs-lookup"><span data-stu-id="71058-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="71058-114">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="71058-114">Overloading</span></span>  
 <span data-ttu-id="71058-115">O [operador&](concatenation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="71058-115">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="71058-116">Sobrecarregar o `&` operador afeta o comportamento do `&=` operador.</span><span class="sxs-lookup"><span data-stu-id="71058-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="71058-117">Se o seu código usa `&=` em uma classe ou estrutura que sobrecarrega, certifique-se de `&` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="71058-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="71058-118">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="71058-118">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71058-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71058-119">Example</span></span>  
 <span data-ttu-id="71058-120">O exemplo a seguir usa o `&=` operador para concatenar duas `String` variáveis e atribuir o resultado à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="71058-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="71058-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="71058-121">See also</span></span>

- [<span data-ttu-id="71058-122">Operador de&</span><span class="sxs-lookup"><span data-stu-id="71058-122">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="71058-123">Operador + =</span><span class="sxs-lookup"><span data-stu-id="71058-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="71058-124">Operadores de atribuição</span><span class="sxs-lookup"><span data-stu-id="71058-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="71058-125">Operadores de concatenação</span><span class="sxs-lookup"><span data-stu-id="71058-125">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="71058-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71058-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="71058-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="71058-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="71058-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="71058-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
