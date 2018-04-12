---
title: '&amp;Operador (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="2821b-102">&amp;Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2821b-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="2821b-103">Gera uma concatenação de cadeia de caracteres de duas expressões.</span><span class="sxs-lookup"><span data-stu-id="2821b-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2821b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2821b-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="2821b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="2821b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="2821b-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2821b-106">Required.</span></span> <span data-ttu-id="2821b-107">Qualquer `String` ou `Object` variável.</span><span class="sxs-lookup"><span data-stu-id="2821b-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="2821b-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2821b-108">Required.</span></span> <span data-ttu-id="2821b-109">Qualquer expressão com um tipo de dados que amplia a `String`.</span><span class="sxs-lookup"><span data-stu-id="2821b-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="2821b-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2821b-110">Required.</span></span> <span data-ttu-id="2821b-111">Qualquer expressão com um tipo de dados que amplia a `String`.</span><span class="sxs-lookup"><span data-stu-id="2821b-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2821b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="2821b-112">Remarks</span></span>  
 <span data-ttu-id="2821b-113">Se o tipo de dados `expression1` ou `expression2` não é `String` mas amplia a `String`, ele será convertido em `String`.</span><span class="sxs-lookup"><span data-stu-id="2821b-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="2821b-114">Se qualquer um dos tipos de dados não se estendem ao `String`, o compilador gerará um erro.</span><span class="sxs-lookup"><span data-stu-id="2821b-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="2821b-115">O tipo de dados `result` é `String`.</span><span class="sxs-lookup"><span data-stu-id="2821b-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="2821b-116">Se uma ou ambas as expressões são avaliadas como [nada](../../../visual-basic/language-reference/nothing.md) ou tem um valor de <xref:System.DBNull.Value?displayProperty=nameWithType>, eles são tratados como uma cadeia de caracteres com um valor de "".</span><span class="sxs-lookup"><span data-stu-id="2821b-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2821b-117">O `&` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="2821b-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2821b-118">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="2821b-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2821b-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2821b-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2821b-120">O caractere e comercial (&) também podem ser usados para identificar variáveis como tipo `Long`.</span><span class="sxs-lookup"><span data-stu-id="2821b-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="2821b-121">Para obter mais informações, consulte [caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="2821b-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2821b-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2821b-122">Example</span></span>  
 <span data-ttu-id="2821b-123">Este exemplo usa o `&` operador para forçar a concatenação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2821b-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="2821b-124">O resultado é um valor de cadeia de caracteres que representa a concatenação dos operandos de cadeia de caracteres de dois.</span><span class="sxs-lookup"><span data-stu-id="2821b-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2821b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2821b-125">See Also</span></span>  
 [<span data-ttu-id="2821b-126">Operador &=</span><span class="sxs-lookup"><span data-stu-id="2821b-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="2821b-127">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="2821b-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="2821b-128">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2821b-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="2821b-129">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="2821b-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="2821b-130">Operadores de concatenação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2821b-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
