---
title: Definindo Classes (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="9efa0-102">Instruções passo a passo: definindo classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9efa0-102">Walkthrough: Defining Classes (Visual Basic)</span></span>
<span data-ttu-id="9efa0-103">Este passo a passo demonstra como definir classes, que você pode usar para criar objetos.</span><span class="sxs-lookup"><span data-stu-id="9efa0-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="9efa0-104">Ele também mostra como adicionar propriedades e métodos para a nova classe e demonstra como inicializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="9efa0-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a><span data-ttu-id="9efa0-105">Para definir uma classe</span><span class="sxs-lookup"><span data-stu-id="9efa0-105">To define a class</span></span>  
  
1.  <span data-ttu-id="9efa0-106">Criar um projeto, clicando em **novo projeto** no **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="9efa0-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="9efa0-107">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="9efa0-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="9efa0-108">Selecione o aplicativo do Windows na lista de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] modelos para exibir o novo projeto do projeto.</span><span class="sxs-lookup"><span data-stu-id="9efa0-108">Select Windows Application from the list of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="9efa0-109">Adicionar uma nova classe ao projeto clicando **Adicionar classe** no **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="9efa0-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="9efa0-110">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="9efa0-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="9efa0-111">Selecione o **classe** modelo.</span><span class="sxs-lookup"><span data-stu-id="9efa0-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="9efa0-112">Nomeie a nova classe `UserNameInfo.vb`e, em seguida, clique em **adicionar** para exibir o código para a nova classe.</span><span class="sxs-lookup"><span data-stu-id="9efa0-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="9efa0-113">Você pode usar o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Editor de códigos** para adicionar uma classe ao seu formulário de inicialização, digitando o `Class` palavra-chave seguido do nome da nova classe.</span><span class="sxs-lookup"><span data-stu-id="9efa0-113">You can use the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="9efa0-114">O **Editor de códigos** fornece correspondente `End Class` instrução para você.</span><span class="sxs-lookup"><span data-stu-id="9efa0-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="9efa0-115">Defina um campo particular para a classe adicionando o seguinte código entre as `Class` e `End Class` instruções:</span><span class="sxs-lookup"><span data-stu-id="9efa0-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     <span data-ttu-id="9efa0-116">Declarar o campo como `Private` significa que ele pode ser usado somente dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="9efa0-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="9efa0-117">Você pode disponibilizar campos de fora de uma classe usando modificadores de acesso, como `Public` que fornecem mais acesso.</span><span class="sxs-lookup"><span data-stu-id="9efa0-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="9efa0-118">Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9efa0-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="9efa0-119">Defina uma propriedade para a classe adicionando o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="9efa0-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  <span data-ttu-id="9efa0-120">Defina um método para a classe adicionando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="9efa0-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. <span data-ttu-id="9efa0-121">Definir um construtor com parâmetros para a nova classe adicionando um procedimento denominado `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="9efa0-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     <span data-ttu-id="9efa0-122">O `Sub New` construtor é chamado automaticamente quando um objeto com base nessa classe é criado.</span><span class="sxs-lookup"><span data-stu-id="9efa0-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="9efa0-123">Este construtor define o valor do campo que contém o nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="9efa0-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
### <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="9efa0-124">Para criar um botão para testar a classe</span><span class="sxs-lookup"><span data-stu-id="9efa0-124">To create a button to test the class</span></span>  
  
1.  <span data-ttu-id="9efa0-125">Alterar o formulário de inicialização para o modo de design clicando com o seu nome na **Solution Explorer** e, em seguida, clicando em **Designer de exibição**.</span><span class="sxs-lookup"><span data-stu-id="9efa0-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="9efa0-126">Por padrão, o formulário de inicialização para projetos de aplicativo do Windows é chamado Form1. vb.</span><span class="sxs-lookup"><span data-stu-id="9efa0-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="9efa0-127">Formulário principal será exibida.</span><span class="sxs-lookup"><span data-stu-id="9efa0-127">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="9efa0-128">Adicione um botão ao formulário principal e clique duas vezes nele para exibir o código para o `Button1_Click` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9efa0-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="9efa0-129">Adicione o seguinte código para chamar o procedimento de teste:</span><span class="sxs-lookup"><span data-stu-id="9efa0-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a><span data-ttu-id="9efa0-130">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="9efa0-130">To run your application</span></span>  
  
1.  <span data-ttu-id="9efa0-131">Execute o aplicativo pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="9efa0-131">Run your application by pressing F5.</span></span> <span data-ttu-id="9efa0-132">Clique no botão no formulário para chamar o procedimento de teste.</span><span class="sxs-lookup"><span data-stu-id="9efa0-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="9efa0-133">Ele exibe uma mensagem informando que o original `UserName` é "MOORE, BOBBY", porque o procedimento chama o `Capitalize` método do objeto.</span><span class="sxs-lookup"><span data-stu-id="9efa0-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="9efa0-134">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="9efa0-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="9efa0-135">O `Button1 Click` procedimento altera o valor da `UserName` propriedade e exibe uma mensagem informando que o novo valor de `UserName` é "Worden, Joe".</span><span class="sxs-lookup"><span data-stu-id="9efa0-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9efa0-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9efa0-136">See Also</span></span>  
 [<span data-ttu-id="9efa0-137">Programação Orientada a Objeto</span><span class="sxs-lookup"><span data-stu-id="9efa0-137">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [<span data-ttu-id="9efa0-138">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="9efa0-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
