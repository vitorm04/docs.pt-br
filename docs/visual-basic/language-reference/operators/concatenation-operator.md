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
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968348"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="75564-102">&amp;Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75564-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="75564-103">Gera uma concatenação de cadeia de caracteres de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="75564-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75564-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75564-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="75564-105">Partes</span><span class="sxs-lookup"><span data-stu-id="75564-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="75564-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="75564-106">Required.</span></span> <span data-ttu-id="75564-107">Qualquer `String` variável `Object` ou.</span><span class="sxs-lookup"><span data-stu-id="75564-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="75564-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="75564-108">Required.</span></span> <span data-ttu-id="75564-109">Qualquer expressão com um tipo de dados que amplia para `String`.</span><span class="sxs-lookup"><span data-stu-id="75564-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="75564-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="75564-110">Required.</span></span> <span data-ttu-id="75564-111">Qualquer expressão com um tipo de dados que amplia para `String`.</span><span class="sxs-lookup"><span data-stu-id="75564-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75564-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="75564-112">Remarks</span></span>  
 <span data-ttu-id="75564-113">Se o tipo de dados `expression1` de `expression2` ou não `String` for, mas se `String`expandir para, ele será `String`convertido em.</span><span class="sxs-lookup"><span data-stu-id="75564-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="75564-114">Se um dos tipos de dados não for ampliado `String`para, o compilador gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="75564-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="75564-115">O tipo de dados `result` de `String`é.</span><span class="sxs-lookup"><span data-stu-id="75564-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="75564-116">Se uma ou ambas as expressões forem avaliadas como [Nothing](../../../visual-basic/language-reference/nothing.md) ou se <xref:System.DBNull.Value?displayProperty=nameWithType>tiverem um valor de, elas serão tratadas como uma cadeia de caracteres com um valor de "".</span><span class="sxs-lookup"><span data-stu-id="75564-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75564-117">O `&` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="75564-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="75564-118">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="75564-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="75564-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="75564-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75564-120">O caractere de e comercial (&) também pode ser usado para identificar variáveis `Long`como tipo.</span><span class="sxs-lookup"><span data-stu-id="75564-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="75564-121">Para obter mais informações, consulte [tipos de caracteres](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="75564-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75564-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="75564-122">Example</span></span>  
 <span data-ttu-id="75564-123">Este exemplo usa o `&` operador para forçar a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="75564-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="75564-124">O resultado é um valor de cadeia de caracteres que representa a concatenação dos dois operandos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="75564-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="75564-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75564-125">See also</span></span>

- [<span data-ttu-id="75564-126">Operador &=</span><span class="sxs-lookup"><span data-stu-id="75564-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="75564-127">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="75564-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="75564-128">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75564-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="75564-129">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="75564-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="75564-130">Operadores de concatenação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75564-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
