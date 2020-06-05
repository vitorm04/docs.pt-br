---
title: Operador ^=
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: e631cc9a484b56ee059449ca1fbd9fc69405333d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371395"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="31c7c-102">Operador ^= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31c7c-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="31c7c-103">Gera o valor de uma variável ou propriedade para a potência de uma expressão e atribui o resultado de volta à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="31c7c-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="31c7c-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="31c7c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="31c7c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="31c7c-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="31c7c-106">Required.</span></span> <span data-ttu-id="31c7c-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="31c7c-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="31c7c-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="31c7c-108">Required.</span></span> <span data-ttu-id="31c7c-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="31c7c-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31c7c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="31c7c-110">Remarks</span></span>  
 <span data-ttu-id="31c7c-111">O elemento no lado esquerdo do `^=` operador pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="31c7c-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="31c7c-112">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="31c7c-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="31c7c-113">O `^=` operador primeiro gera o valor da variável ou da propriedade (no lado esquerdo do operador) para a potência do valor da expressão (no lado direito do operador)....</span><span class="sxs-lookup"><span data-stu-id="31c7c-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="31c7c-114">Em seguida, o operador atribui o resultado dessa operação de volta à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="31c7c-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="31c7c-115">Visual Basic sempre executa exponenciação no [tipo de dados Double](../data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="31c7c-115">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span> <span data-ttu-id="31c7c-116">Os operandos de qualquer tipo diferente são convertidos em `Double` e o resultado é sempre `Double` .</span><span class="sxs-lookup"><span data-stu-id="31c7c-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="31c7c-117">O valor de `expression` pode ser fracionário, negativo ou ambos.</span><span class="sxs-lookup"><span data-stu-id="31c7c-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="31c7c-118">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="31c7c-118">Overloading</span></span>  
 <span data-ttu-id="31c7c-119">O [operador ^](exponentiation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="31c7c-119">The [^ Operator](exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="31c7c-120">Sobrecarregar o `^` operador afeta o comportamento do `^=` operador.</span><span class="sxs-lookup"><span data-stu-id="31c7c-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="31c7c-121">Se o seu código usa `^=` em uma classe ou estrutura que sobrecarrega, certifique-se de `^` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="31c7c-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="31c7c-122">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="31c7c-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31c7c-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31c7c-123">Example</span></span>  
 <span data-ttu-id="31c7c-124">O exemplo a seguir usa o `^=` operador para aumentar o valor de uma `Integer` variável para a potência de uma segunda variável e atribuir o resultado à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="31c7c-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="31c7c-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="31c7c-125">See also</span></span>

- [<span data-ttu-id="31c7c-126">Operador ^</span><span class="sxs-lookup"><span data-stu-id="31c7c-126">^ Operator</span></span>](exponentiation-operator.md)
- [<span data-ttu-id="31c7c-127">Operadores de atribuição</span><span class="sxs-lookup"><span data-stu-id="31c7c-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="31c7c-128">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="31c7c-128">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="31c7c-129">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31c7c-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="31c7c-130">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="31c7c-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="31c7c-131">Instruções</span><span class="sxs-lookup"><span data-stu-id="31c7c-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
