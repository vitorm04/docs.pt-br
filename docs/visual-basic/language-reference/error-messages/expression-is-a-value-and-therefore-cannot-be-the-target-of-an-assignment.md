---
title: Expressão é um valor e, por isso, não pode ser o destino de uma atribuição
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: cd23e6c2beb2f93578a350bc41a780c9ab785f26
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160887"
---
# <a name="bc30068-expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="c0463-102">BC30068: Expression é um valor e, portanto, não pode ser o destino de uma atribuição</span><span class="sxs-lookup"><span data-stu-id="c0463-102">BC30068: Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="c0463-103">Uma instrução tenta atribuir um valor a uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c0463-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="c0463-104">Você pode atribuir um valor somente a uma variável, propriedade ou elemento de matriz gravável em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c0463-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="c0463-105">O exemplo a seguir ilustra como esse erro pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="c0463-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="c0463-106">Exemplos semelhantes podem ser aplicados a propriedades e elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="c0463-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="c0463-107">**Acesso indireto.**</span><span class="sxs-lookup"><span data-stu-id="c0463-107">**Indirect Access.**</span></span> <span data-ttu-id="c0463-108">O acesso indireto por meio de um tipo de valor também pode gerar esse erro.</span><span class="sxs-lookup"><span data-stu-id="c0463-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="c0463-109">Considere o exemplo de código a seguir, que tenta definir o valor de <xref:System.Drawing.Point> acessando-o indiretamente por meio de <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="c0463-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="c0463-110">A última instrução do exemplo anterior falha porque ela cria apenas uma alocação temporária para a <xref:System.Drawing.Point> estrutura retornada pela <xref:System.Windows.Forms.Control.Location%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="c0463-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="c0463-111">Uma estrutura é um tipo de valor e a estrutura temporária não é mantida após a execução da instrução.</span><span class="sxs-lookup"><span data-stu-id="c0463-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="c0463-112">O problema é resolvido declarando e usando uma variável para <xref:System.Windows.Forms.Control.Location%2A> , que cria uma alocação mais permanente para a <xref:System.Drawing.Point> estrutura.</span><span class="sxs-lookup"><span data-stu-id="c0463-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="c0463-113">O exemplo a seguir mostra o código que pode substituir a última instrução do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="c0463-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="c0463-114">**ID do erro:** BC30068</span><span class="sxs-lookup"><span data-stu-id="c0463-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c0463-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c0463-115">To correct this error</span></span>

- <span data-ttu-id="c0463-116">Se a instrução atribuir um valor a uma expressão, substitua a expressão por uma única variável, propriedade ou elemento de matriz gravável.</span><span class="sxs-lookup"><span data-stu-id="c0463-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="c0463-117">Se a instrução fizer acesso indireto por meio de um tipo de valor (geralmente uma estrutura), crie uma variável para conter o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="c0463-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="c0463-118">Atribua a estrutura apropriada (ou outro tipo de valor) à variável.</span><span class="sxs-lookup"><span data-stu-id="c0463-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="c0463-119">Use a variável para acessar a propriedade para atribuir um valor a ela.</span><span class="sxs-lookup"><span data-stu-id="c0463-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0463-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="c0463-120">See also</span></span>

- [<span data-ttu-id="c0463-121">Operadores e expressões</span><span class="sxs-lookup"><span data-stu-id="c0463-121">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="c0463-122">Instruções</span><span class="sxs-lookup"><span data-stu-id="c0463-122">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="c0463-123">Solucionando problemas de procedimentos</span><span class="sxs-lookup"><span data-stu-id="c0463-123">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
