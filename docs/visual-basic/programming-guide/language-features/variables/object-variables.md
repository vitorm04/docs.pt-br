---
title: Variáveis de objeto
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351790"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="7d1d0-102">Variáveis de objeto no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d1d0-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="7d1d0-103">Além de armazenar valores diretamente, uma variável pode se referir a um objeto.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="7d1d0-104">Você atribui um objeto a uma variável pelos mesmos motivos para atribuir qualquer valor a uma variável:</span><span class="sxs-lookup"><span data-stu-id="7d1d0-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="7d1d0-105">Um nome de variável é frequentemente mais curto e mais fácil de lembrar do que o caminho completo dos métodos e propriedades necessários para acessar o próprio objeto.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="7d1d0-106">O uso de uma variável que se refere a um objeto é mais eficiente do que acessar repetidamente o próprio objeto por meio dos métodos ou Propriedades necessários.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="7d1d0-107">Você pode alterar uma variável para fazer referência a outros objetos enquanto seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="7d1d0-108">Tornando o código mais curto</span><span class="sxs-lookup"><span data-stu-id="7d1d0-108">Making Code Shorter</span></span>

<span data-ttu-id="7d1d0-109">Você pode usar variáveis de objeto para encurtar o código que você precisa digitar.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="7d1d0-110">O exemplo a seguir usa o caminho completo de métodos e propriedades para acessar um objeto <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="7d1d0-111">Você pode encurtar esse código e acelerar a execução, se você usar uma variável de objeto para o controle.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="7d1d0-112">Você deve declarar a variável de objeto com a classe específica que pretende atribuir a ela (`Control` nesse caso).</span><span class="sxs-lookup"><span data-stu-id="7d1d0-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="7d1d0-113">Depois de atribuir um objeto à variável, você pode tratá-lo exatamente como trata o objeto ao qual ele se refere.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="7d1d0-114">Você pode definir ou recuperar as propriedades do objeto ou usar qualquer um de seus métodos.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="7d1d0-115">O exemplo a seguir usa uma variável de objeto para simplificar o código no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="7d1d0-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="7d1d0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d1d0-116">See also</span></span>

- [<span data-ttu-id="7d1d0-117">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="7d1d0-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="7d1d0-118">Como agilizar o acesso a um objeto com um demarcador de qualificação longo</span><span class="sxs-lookup"><span data-stu-id="7d1d0-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="7d1d0-119">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="7d1d0-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="7d1d0-120">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="7d1d0-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="7d1d0-121">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="7d1d0-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
