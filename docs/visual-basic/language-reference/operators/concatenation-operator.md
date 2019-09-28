---
title: '&amp;Operador (Visual Basic)'
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
ms.openlocfilehash: aaa7c1b9ab7f6c920180d97b55c3bdeb23f00e02
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592239"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="effd8-102">&amp;Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="effd8-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="effd8-103">Gera uma concatenação de cadeia de caracteres de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="effd8-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effd8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="effd8-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="effd8-105">Partes</span><span class="sxs-lookup"><span data-stu-id="effd8-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="effd8-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="effd8-106">Required.</span></span> <span data-ttu-id="effd8-107">Qualquer variável `String` ou `Object`.</span><span class="sxs-lookup"><span data-stu-id="effd8-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="effd8-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="effd8-108">Required.</span></span> <span data-ttu-id="effd8-109">Qualquer expressão com um tipo de dados que amplia para `String`.</span><span class="sxs-lookup"><span data-stu-id="effd8-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="effd8-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="effd8-110">Required.</span></span> <span data-ttu-id="effd8-111">Qualquer expressão com um tipo de dados que amplia para `String`.</span><span class="sxs-lookup"><span data-stu-id="effd8-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="effd8-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="effd8-112">Remarks</span></span>  
 <span data-ttu-id="effd8-113">Se o tipo de dados de `expression1` ou `expression2` não for `String`, mas for ampliado para `String`, ele será convertido em `String`.</span><span class="sxs-lookup"><span data-stu-id="effd8-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="effd8-114">Se um dos tipos de dados não for ampliado para `String`, o compilador gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="effd8-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="effd8-115">O tipo de dados de `result` é `String`.</span><span class="sxs-lookup"><span data-stu-id="effd8-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="effd8-116">Se uma ou ambas as expressões forem avaliadas como [Nothing](../../../visual-basic/language-reference/nothing.md) ou se tiverem um valor de <xref:System.DBNull.Value?displayProperty=nameWithType>, elas serão tratadas como uma cadeia de caracteres com um valor de "".</span><span class="sxs-lookup"><span data-stu-id="effd8-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="effd8-117">O operador `&` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="effd8-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="effd8-118">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="effd8-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="effd8-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="effd8-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="effd8-120">O caractere de e comercial (&) também pode ser usado para identificar variáveis como tipo `Long`.</span><span class="sxs-lookup"><span data-stu-id="effd8-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="effd8-121">Para obter mais informações, consulte [tipos de caracteres](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="effd8-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="effd8-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="effd8-122">Example</span></span>  
 <span data-ttu-id="effd8-123">Este exemplo usa o operador `&` para forçar a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="effd8-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="effd8-124">O resultado é um valor de cadeia de caracteres que representa a concatenação dos dois operandos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="effd8-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="effd8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="effd8-125">See also</span></span>

- [<span data-ttu-id="effd8-126">Operador &=</span><span class="sxs-lookup"><span data-stu-id="effd8-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="effd8-127">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="effd8-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="effd8-128">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="effd8-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="effd8-129">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="effd8-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="effd8-130">Operadores de concatenação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="effd8-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
