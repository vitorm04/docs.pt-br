---
title: O tipo de '<variablename>' não pode ser inferido porque os limites de loop e a variável step não são ampliados com o mesmo tipo
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512714"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="82657-102">O tipo de\<' VariableName > ' não pode ser inferido porque os limites do loop e a variável Step não se ampliam ao mesmo tipo</span><span class="sxs-lookup"><span data-stu-id="82657-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="82657-103">Você escreveu um `For...Next` loop no qual o compilador não pode inferir um tipo de dados para a variável de controle de loop porque as seguintes condições são verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="82657-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="82657-104">O tipo de dados da variável de controle de loop não é especificado `As` com uma cláusula.</span><span class="sxs-lookup"><span data-stu-id="82657-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="82657-105">Os limites do loop e a variável Step contêm pelo menos dois tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="82657-105">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="82657-106">Não existem conversões padrão entre os tipos de dados.</span><span class="sxs-lookup"><span data-stu-id="82657-106">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="82657-107">Portanto, o compilador não pode inferir o tipo de dados da variável de controle de um loop.</span><span class="sxs-lookup"><span data-stu-id="82657-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="82657-108">No exemplo a seguir, a variável Step é um caractere e os limites do loop são inteiros.</span><span class="sxs-lookup"><span data-stu-id="82657-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="82657-109">Como não há conversão padrão entre caracteres e inteiros, esse erro é relatado.</span><span class="sxs-lookup"><span data-stu-id="82657-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="82657-110">**ID do erro:** BC30982</span><span class="sxs-lookup"><span data-stu-id="82657-110">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="82657-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="82657-111">To correct this error</span></span>

- <span data-ttu-id="82657-112">Altere os tipos dos limites do loop e da variável Step conforme necessário para que pelo menos um deles seja um tipo que os outros ampliam.</span><span class="sxs-lookup"><span data-stu-id="82657-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="82657-113">No exemplo anterior, altere o tipo de `stepVar` para. `Integer`</span><span class="sxs-lookup"><span data-stu-id="82657-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="82657-114">- ou -</span><span class="sxs-lookup"><span data-stu-id="82657-114">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="82657-115">Use funções de conversão explícitas para converter os limites do loop e a variável Step para os tipos apropriados.</span><span class="sxs-lookup"><span data-stu-id="82657-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="82657-116">No exemplo anterior, aplique a `Val` função a. `stepVar`</span><span class="sxs-lookup"><span data-stu-id="82657-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="82657-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82657-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="82657-118">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="82657-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="82657-119">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="82657-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="82657-120">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="82657-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="82657-121">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="82657-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="82657-122">Funções de Conversão do Tipo</span><span class="sxs-lookup"><span data-stu-id="82657-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="82657-123">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="82657-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
