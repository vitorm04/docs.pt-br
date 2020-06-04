---
title: Variáveis de objeto
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410329"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="6a7c2-102">Variáveis de objeto no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a7c2-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="6a7c2-103">Além de armazenar valores diretamente, uma variável pode se referir a um objeto.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="6a7c2-104">Você atribui um objeto a uma variável pelos mesmos motivos para atribuir qualquer valor a uma variável:</span><span class="sxs-lookup"><span data-stu-id="6a7c2-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="6a7c2-105">Um nome de variável é frequentemente mais curto e mais fácil de lembrar do que o caminho completo dos métodos e propriedades necessários para acessar o próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="6a7c2-106">O uso de uma variável que se refere a um objeto é mais eficiente do que acessar repetidamente o próprio objeto por meio dos métodos ou Propriedades necessários.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="6a7c2-107">Você pode alterar uma variável para fazer referência a outros objetos enquanto seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="6a7c2-108">Tornando o código mais curto</span><span class="sxs-lookup"><span data-stu-id="6a7c2-108">Making Code Shorter</span></span>

<span data-ttu-id="6a7c2-109">Você pode usar variáveis de objeto para encurtar o código que você precisa digitar.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="6a7c2-110">O exemplo a seguir usa o caminho completo de métodos e propriedades para acessar um <xref:System.Windows.Forms.Control> objeto.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="6a7c2-111">Você pode encurtar esse código e acelerar a execução, se você usar uma variável de objeto para o controle.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="6a7c2-112">Você deve declarar a variável de objeto com a classe específica que pretende atribuir a ela ( `Control` nesse caso).</span><span class="sxs-lookup"><span data-stu-id="6a7c2-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="6a7c2-113">Depois de atribuir um objeto à variável, você pode tratá-lo exatamente como trata o objeto ao qual ele se refere.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="6a7c2-114">Você pode definir ou recuperar as propriedades do objeto ou usar qualquer um de seus métodos.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="6a7c2-115">O exemplo a seguir usa uma variável de objeto para simplificar o código no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="6a7c2-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="6a7c2-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6a7c2-116">See also</span></span>

- [<span data-ttu-id="6a7c2-117">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="6a7c2-117">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="6a7c2-118">Como agilizar o acesso a um objeto com um caminho de qualificação longo</span><span class="sxs-lookup"><span data-stu-id="6a7c2-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="6a7c2-119">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="6a7c2-119">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="6a7c2-120">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="6a7c2-120">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="6a7c2-121">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="6a7c2-121">Object Variable Values</span></span>](object-variable-values.md)
