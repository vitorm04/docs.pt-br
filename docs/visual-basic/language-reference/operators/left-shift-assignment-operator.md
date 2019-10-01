---
title: < < = operador (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: aae71069bdcb88efa5842526dd7eb47806f248d0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701103"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="febb9-102">\< @ no__t-1 = operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="febb9-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="febb9-103">Executa um deslocamento aritmético para a esquerda no valor de uma variável ou propriedade e atribui o resultado de volta à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="febb9-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="febb9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="febb9-104">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="febb9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="febb9-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="febb9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="febb9-106">Required.</span></span> <span data-ttu-id="febb9-107">Variável ou propriedade de um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` ou `ULong`).</span><span class="sxs-lookup"><span data-stu-id="febb9-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="febb9-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="febb9-108">Required.</span></span> <span data-ttu-id="febb9-109">Expressão numérica de um tipo de dados que amplia para `Integer`.</span><span class="sxs-lookup"><span data-stu-id="febb9-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="febb9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="febb9-110">Remarks</span></span>  
 <span data-ttu-id="febb9-111">O elemento no lado esquerdo do operador `<<=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="febb9-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="febb9-112">A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="febb9-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="febb9-113">O operador `<<=` primeiro executa um deslocamento aritmético para a esquerda no valor da variável ou da propriedade.</span><span class="sxs-lookup"><span data-stu-id="febb9-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="febb9-114">Em seguida, o operador atribui o resultado dessa operação de volta para essa variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="febb9-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="febb9-115">Deslocamentos aritméticos não são circulares, o que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="febb9-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="febb9-116">Em um deslocamento aritmético à esquerda, os bits deslocados além do intervalo do tipo de dados de resultado são descartados e as posições de bits vagadas à direita são definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="febb9-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="febb9-117">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="febb9-117">Overloading</span></span>  
 <span data-ttu-id="febb9-118">O [operador de < de <](../../../visual-basic/language-reference/operators/left-shift-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="febb9-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="febb9-119">Sobrecarregar o operador `<<` afeta o comportamento do operador `<<=`.</span><span class="sxs-lookup"><span data-stu-id="febb9-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="febb9-120">Se seu código usar `<<=` em uma classe ou estrutura que sobrecarrega `<<`, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="febb9-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="febb9-121">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="febb9-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="febb9-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="febb9-122">Example</span></span>  
 <span data-ttu-id="febb9-123">O exemplo a seguir usa o operador `<<=` para deslocar o padrão de bit de uma variável `Integer` Left pelo valor especificado e atribuir o resultado à variável.</span><span class="sxs-lookup"><span data-stu-id="febb9-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="febb9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="febb9-124">See also</span></span>

- [<span data-ttu-id="febb9-125">Operador <<</span><span class="sxs-lookup"><span data-stu-id="febb9-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="febb9-126">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="febb9-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="febb9-127">Operadores Bit Shift</span><span class="sxs-lookup"><span data-stu-id="febb9-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="febb9-128">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="febb9-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="febb9-129">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="febb9-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="febb9-130">Instruções</span><span class="sxs-lookup"><span data-stu-id="febb9-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
