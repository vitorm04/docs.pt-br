---
title: '>>Operador ='
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: a1c2331791644155504183d3cf5767470a3bf17b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873351"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bb760-102">Operador >>= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb760-102">>>= Operator (Visual Basic)</span></span>

<span data-ttu-id="bb760-103">Executa um deslocamento aritmético para a direita no valor de uma variável ou propriedade e atribui o resultado de volta à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="bb760-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb760-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb760-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="bb760-105">Partes</span><span class="sxs-lookup"><span data-stu-id="bb760-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="bb760-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bb760-106">Required.</span></span> <span data-ttu-id="bb760-107">Variável ou propriedade de um tipo integral ( `SByte` ,,,,, `Byte` `Short` `UShort` `Integer` `UInteger` , `Long` ou `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="bb760-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="bb760-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bb760-108">Required.</span></span> <span data-ttu-id="bb760-109">Expressão numérica de um tipo de dados que amplia para `Integer` .</span><span class="sxs-lookup"><span data-stu-id="bb760-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb760-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb760-110">Remarks</span></span>  

 <span data-ttu-id="bb760-111">O elemento no lado esquerdo do `>>=` operador pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="bb760-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bb760-112">A variável ou a propriedade não pode ser [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="bb760-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="bb760-113">O `>>=` operador primeiro executa um deslocamento aritmético à direita no valor da variável ou da propriedade.</span><span class="sxs-lookup"><span data-stu-id="bb760-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="bb760-114">Em seguida, o operador atribui o resultado dessa operação de volta à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="bb760-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="bb760-115">Deslocamentos aritméticos não são circulares, o que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="bb760-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="bb760-116">Em um deslocamento aritmético à direita, os bits deslocados além da posição de bits mais à direita são descartados e o bit mais à esquerda é propagado para as posições de bits vagas à esquerda.</span><span class="sxs-lookup"><span data-stu-id="bb760-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="bb760-117">Isso significa que `variableorproperty` , se o tiver um valor negativo, as posições vagas serão definidas como um.</span><span class="sxs-lookup"><span data-stu-id="bb760-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="bb760-118">Se `variableorproperty` for positivo ou se seu tipo de dados for um tipo não assinado, as posições vagadas serão definidas como zero.</span><span class="sxs-lookup"><span data-stu-id="bb760-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bb760-119">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="bb760-119">Overloading</span></span>  

 <span data-ttu-id="bb760-120">O [ operador>> ](right-shift-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="bb760-120">The [>> Operator](right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bb760-121">Sobrecarregar o `>>` operador afeta o comportamento do `>>=` operador.</span><span class="sxs-lookup"><span data-stu-id="bb760-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="bb760-122">Se o seu código usa `>>=` em uma classe ou estrutura que sobrecarrega, certifique-se de `>>` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="bb760-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bb760-123">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bb760-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb760-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bb760-124">Example</span></span>  

 <span data-ttu-id="bb760-125">O exemplo a seguir usa o `>>=` operador para deslocar o padrão de bits de uma `Integer` variável pelo valor especificado e atribuir o resultado à variável.</span><span class="sxs-lookup"><span data-stu-id="bb760-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="bb760-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb760-126">See also</span></span>

- [<span data-ttu-id="bb760-127"> Operador de>> </span><span class="sxs-lookup"><span data-stu-id="bb760-127">>> Operator</span></span>](right-shift-operator.md)
- [<span data-ttu-id="bb760-128">Operadores de atribuição</span><span class="sxs-lookup"><span data-stu-id="bb760-128">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="bb760-129">Operadores Bit Shift</span><span class="sxs-lookup"><span data-stu-id="bb760-129">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="bb760-130">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb760-130">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="bb760-131">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="bb760-131">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="bb760-132">Instruções</span><span class="sxs-lookup"><span data-stu-id="bb760-132">Statements</span></span>](../../programming-guide/language-features/statements.md)
