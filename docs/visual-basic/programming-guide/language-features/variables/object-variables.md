---
title: Variáveis de objeto no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: cc5be13293a89e73d1790e94a99d7936f1711e12
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352965"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="4d2ae-102">Variáveis de objeto no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d2ae-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="4d2ae-103">Além de armazenar valores diretamente, uma variável pode se referir a um objeto.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="4d2ae-104">Você pode atribuir um objeto a uma variável pelas mesmas razões que atribuir qualquer valor a uma variável:</span><span class="sxs-lookup"><span data-stu-id="4d2ae-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="4d2ae-105">Um nome de variável é geralmente mais curta e fácil de lembrar que o caminho completo de métodos e propriedades necessárias para acessar o objeto em si.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="4d2ae-106">Usando uma variável que faz referência a um objeto é mais eficiente do que repetidamente acessar o objeto em si por meio de métodos ou propriedades necessários.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="4d2ae-107">Você pode alterar uma variável para fazer referência a outros objetos enquanto seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="4d2ae-108">Tornar o código mais curto</span><span class="sxs-lookup"><span data-stu-id="4d2ae-108">Making Code Shorter</span></span>

<span data-ttu-id="4d2ae-109">Você pode usar variáveis de objeto para diminuir o código que você tem que digitar.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="4d2ae-110">O exemplo a seguir usa o caminho completo de métodos e propriedades para acessar um <xref:System.Windows.Forms.Control> objeto.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="4d2ae-111">Você pode reduzir esse código e acelerar a execução, se você usar uma variável de objeto para o controle.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="4d2ae-112">Você deve declarar a variável de objeto com a classe específica que você pretende atribuir a ela (`Control` nesse caso).</span><span class="sxs-lookup"><span data-stu-id="4d2ae-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="4d2ae-113">Depois de atribuir um objeto à variável, você pode tratá-lo exatamente conforme você tratar o objeto ao qual se refere.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="4d2ae-114">Você pode definir ou recuperar as propriedades do objeto ou usar qualquer um dos seus métodos.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="4d2ae-115">O exemplo a seguir usa uma variável de objeto para simplificar o código no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="4d2ae-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d2ae-116">See also</span></span>

- [<span data-ttu-id="4d2ae-117">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="4d2ae-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="4d2ae-118">Como: Acelerar o acesso a um objeto com um demarcador de qualificação longo</span><span class="sxs-lookup"><span data-stu-id="4d2ae-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="4d2ae-119">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="4d2ae-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="4d2ae-120">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="4d2ae-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="4d2ae-121">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="4d2ae-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
