---
title: "Variáveis de objeto no Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44689d649a381618e5d6c934deb2b7b9bea463ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="418bf-102">Variáveis de objeto no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="418bf-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="418bf-103">Além de armazenar valores diretamente, uma variável pode se referir a um objeto.</span><span class="sxs-lookup"><span data-stu-id="418bf-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="418bf-104">Você pode atribuir um objeto a uma variável pelos mesmos motivos que você atribui qualquer valor a uma variável:</span><span class="sxs-lookup"><span data-stu-id="418bf-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="418bf-105">Um nome de variável é geralmente mais curta e fácil de lembrar que o caminho completo de métodos e propriedades necessárias para acessar o objeto propriamente dito.</span><span class="sxs-lookup"><span data-stu-id="418bf-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="418bf-106">Usando uma variável que faz referência a um objeto é mais eficiente do que repetidamente acessar o próprio objeto por meio de métodos ou propriedades necessários.</span><span class="sxs-lookup"><span data-stu-id="418bf-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="418bf-107">Você pode alterar uma variável para fazer referência a outros objetos enquanto seu código está em execução.</span><span class="sxs-lookup"><span data-stu-id="418bf-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="418bf-108">Tornando o código menor</span><span class="sxs-lookup"><span data-stu-id="418bf-108">Making Code Shorter</span></span>  
 <span data-ttu-id="418bf-109">Você pode usar variáveis de objeto para diminuir o código que você tem que digitar.</span><span class="sxs-lookup"><span data-stu-id="418bf-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="418bf-110">O exemplo a seguir usa o caminho completo de métodos e propriedades para acessar um <xref:System.Windows.Forms.Control> objeto.</span><span class="sxs-lookup"><span data-stu-id="418bf-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="418bf-111">Você pode reduzir esse código e acelerar a execução, se você usar uma variável de objeto para o controle.</span><span class="sxs-lookup"><span data-stu-id="418bf-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="418bf-112">Você deve declarar a variável de objeto com a classe específica que você pretende atribuir a ela (`Control` nesse caso).</span><span class="sxs-lookup"><span data-stu-id="418bf-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="418bf-113">Depois de atribuir um objeto à variável, você pode tratá-la exatamente como tratar o objeto ao qual ela se refere.</span><span class="sxs-lookup"><span data-stu-id="418bf-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="418bf-114">Você pode definir ou recuperar as propriedades do objeto ou usar qualquer um dos seus métodos.</span><span class="sxs-lookup"><span data-stu-id="418bf-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="418bf-115">O exemplo a seguir usa uma variável de objeto para simplificar o código no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="418bf-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="418bf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="418bf-116">See Also</span></span>  
 [<span data-ttu-id="418bf-117">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="418bf-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="418bf-118">Como agilizar o acesso a um objeto com um demarcador de qualificação longo</span><span class="sxs-lookup"><span data-stu-id="418bf-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="418bf-119">Declaração de Variável do Objeto</span><span class="sxs-lookup"><span data-stu-id="418bf-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="418bf-120">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="418bf-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="418bf-121">Valores de Variável de Objeto</span><span class="sxs-lookup"><span data-stu-id="418bf-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
