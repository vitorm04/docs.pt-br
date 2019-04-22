---
title: '&amp; Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: dd85363447e9b405241d608550d9484b4760a739
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817273"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="8e471-102">&amp; Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e471-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="8e471-103">Gera uma concatenação de cadeia de caracteres de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="8e471-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e471-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e471-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="8e471-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8e471-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="8e471-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8e471-106">Required.</span></span> <span data-ttu-id="8e471-107">Qualquer `String` ou `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="8e471-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="8e471-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8e471-108">Required.</span></span> <span data-ttu-id="8e471-109">Qualquer expressão com um tipo de dados que amplia a `String`.</span><span class="sxs-lookup"><span data-stu-id="8e471-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="8e471-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8e471-110">Required.</span></span> <span data-ttu-id="8e471-111">Qualquer expressão com um tipo de dados que amplia a `String`.</span><span class="sxs-lookup"><span data-stu-id="8e471-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e471-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e471-112">Remarks</span></span>  
 <span data-ttu-id="8e471-113">Se o tipo de dados `expression1` ou `expression2` não está `String` , mas é ampliado para `String`, ele será convertido em `String`.</span><span class="sxs-lookup"><span data-stu-id="8e471-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="8e471-114">Se qualquer um dos tipos de dados não se estendem ao `String`, o compilador gera um erro.</span><span class="sxs-lookup"><span data-stu-id="8e471-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="8e471-115">O tipo de dados `result` é `String`.</span><span class="sxs-lookup"><span data-stu-id="8e471-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="8e471-116">Se uma ou ambas as expressões são avaliadas como [nada](../../../visual-basic/language-reference/nothing.md) ou ter um valor de <xref:System.DBNull.Value?displayProperty=nameWithType>, eles são tratados como uma cadeia de caracteres com um valor de "".</span><span class="sxs-lookup"><span data-stu-id="8e471-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e471-117">O `&` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="8e471-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8e471-118">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="8e471-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8e471-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8e471-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e471-120">O caractere e comercial (&) também podem ser usados para identificar variáveis como tipo `Long`.</span><span class="sxs-lookup"><span data-stu-id="8e471-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="8e471-121">Para obter mais informações, consulte [caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="8e471-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e471-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8e471-122">Example</span></span>  
 <span data-ttu-id="8e471-123">Este exemplo usa o `&` operador para forçar a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8e471-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="8e471-124">O resultado é um valor de cadeia de caracteres que representa a concatenação dos operandos de cadeia de caracteres de dois.</span><span class="sxs-lookup"><span data-stu-id="8e471-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8e471-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e471-125">See also</span></span>

- [<span data-ttu-id="8e471-126">Operador &=</span><span class="sxs-lookup"><span data-stu-id="8e471-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="8e471-127">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="8e471-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="8e471-128">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e471-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8e471-129">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="8e471-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8e471-130">Operadores de concatenação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e471-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
