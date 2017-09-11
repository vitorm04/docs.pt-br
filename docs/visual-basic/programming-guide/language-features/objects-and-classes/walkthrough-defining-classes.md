---
title: Definindo Classes (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5b470b8ba9b60dfb1cd1bbb207e02217f5311c27
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="25595-102">Instruções passo a passo: definindo classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25595-102">Walkthrough: Defining Classes (Visual Basic)</span></span>
<span data-ttu-id="25595-103">Este passo a passo demonstra como definir classes, que você pode usar para criar objetos.</span><span class="sxs-lookup"><span data-stu-id="25595-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="25595-104">Ele também mostra como adicionar propriedades e métodos para a nova classe e demonstra como inicializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="25595-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a><span data-ttu-id="25595-105">Para definir uma classe</span><span class="sxs-lookup"><span data-stu-id="25595-105">To define a class</span></span>  
  
1.  <span data-ttu-id="25595-106">Criar um projeto, clicando em **novo projeto** sobre o **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="25595-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="25595-107">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="25595-107">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="25595-108">Selecione o aplicativo do Windows na lista de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] modelos para exibir o novo projeto de projeto.</span><span class="sxs-lookup"><span data-stu-id="25595-108">Select Windows Application from the list of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates to display the new project.</span></span>  
  
3.  <span data-ttu-id="25595-109">Adicione uma nova classe ao projeto, clicando em **Add Class** sobre o **projeto** menu.</span><span class="sxs-lookup"><span data-stu-id="25595-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="25595-110">O **Adicionar Novo Item** caixa de diálogo é exibida.</span><span class="sxs-lookup"><span data-stu-id="25595-110">The **Add New Item** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="25595-111">Selecione o **classe** modelo.</span><span class="sxs-lookup"><span data-stu-id="25595-111">Select the **Class** template.</span></span>  
  
5.  <span data-ttu-id="25595-112">Nomeie a nova classe `UserNameInfo.vb`e, em seguida, clique em **adicionar** para exibir o código para a nova classe.</span><span class="sxs-lookup"><span data-stu-id="25595-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     <span data-ttu-id="25595-113">[!code-vb[VbVbalrOOP n º&5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="25595-113">[!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="25595-114">Você pode usar o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Editor de códigos** para adicionar uma classe ao seu formulário de inicialização, digitando a `Class` palavra-chave seguido do nome da nova classe.</span><span class="sxs-lookup"><span data-stu-id="25595-114">You can use the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="25595-115">O **Editor de códigos** fornece um correspondente `End Class` instrução para você.</span><span class="sxs-lookup"><span data-stu-id="25595-115">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6.  <span data-ttu-id="25595-116">Defina um campo particular para a classe adicionando o seguinte código entre o `Class` e `End Class` instruções:</span><span class="sxs-lookup"><span data-stu-id="25595-116">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     <span data-ttu-id="25595-117">[!code-vb[VbVbalrOOP&#7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="25595-117">[!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]</span></span>  
  
     <span data-ttu-id="25595-118">Declarar o campo como `Private` significa que ele pode ser usado somente dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="25595-118">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="25595-119">Você pode disponibilizar campos de fora de uma classe usando modificadores de acesso, como `Public` que fornecem mais acesso.</span><span class="sxs-lookup"><span data-stu-id="25595-119">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="25595-120">Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="25595-120">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7.  <span data-ttu-id="25595-121">Defina uma propriedade para a classe adicionando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="25595-121">Define a property for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="25595-122">[!code-vb[VbVbalrOOP n º&8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="25595-122">[!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]</span></span>  
  
8.  <span data-ttu-id="25595-123">Defina um método para a classe adicionando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="25595-123">Define a method for the class by adding the following code:</span></span>  
  
     <span data-ttu-id="25595-124">[!code-vb[VbVbalrOOP n º&9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="25595-124">[!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]</span></span>  
  
9. <span data-ttu-id="25595-125">Defina um construtor com parâmetros para a nova classe adicionando um procedimento denominado `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="25595-125">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     <span data-ttu-id="25595-126">[!code-vb[VbVbalrOOP n º&10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="25595-126">[!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]</span></span>  
  
     <span data-ttu-id="25595-127">O `Sub New` construtor é chamado automaticamente quando um objeto baseado nessa classe é criado.</span><span class="sxs-lookup"><span data-stu-id="25595-127">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="25595-128">Esse construtor define o valor do campo que contém o nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="25595-128">This constructor sets the value of the field that holds the user name.</span></span>  
  
### <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="25595-129">Para criar um botão para testar a classe</span><span class="sxs-lookup"><span data-stu-id="25595-129">To create a button to test the class</span></span>  
  
1.  <span data-ttu-id="25595-130">Alterar o formulário de inicialização para o modo design clicando em seu nome na **Solution Explorer** e, em seguida, clicando em **View Designer**.</span><span class="sxs-lookup"><span data-stu-id="25595-130">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="25595-131">Por padrão, o formulário de inicialização para projetos de aplicativos do Windows é chamado Form1. vb.</span><span class="sxs-lookup"><span data-stu-id="25595-131">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="25595-132">O formulário principal será exibida.</span><span class="sxs-lookup"><span data-stu-id="25595-132">The main form will then appear.</span></span>  
  
2.  <span data-ttu-id="25595-133">Adicione um botão ao formulário principal e clique duas vezes nele para exibir o código para o `Button1_Click` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="25595-133">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="25595-134">Adicione o seguinte código para chamar o procedimento de teste:</span><span class="sxs-lookup"><span data-stu-id="25595-134">Add the following code to call the test procedure:</span></span>  
  
     <span data-ttu-id="25595-135">[!code-vb[VbVbalrOOP&#12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="25595-135">[!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]</span></span>  
  
### <a name="to-run-your-application"></a><span data-ttu-id="25595-136">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="25595-136">To run your application</span></span>  
  
1.  <span data-ttu-id="25595-137">Execute o aplicativo pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="25595-137">Run your application by pressing F5.</span></span> <span data-ttu-id="25595-138">Clique no botão no formulário para chamar o procedimento de teste.</span><span class="sxs-lookup"><span data-stu-id="25595-138">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="25595-139">Exibe uma mensagem informando que o original `UserName` é "MOORE, BOBBY", porque o procedimento chama o `Capitalize` método do objeto.</span><span class="sxs-lookup"><span data-stu-id="25595-139">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2.  <span data-ttu-id="25595-140">Clique em **Okey** para descartar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="25595-140">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="25595-141">O `Button1 Click` procedimento altera o valor da `UserName` propriedade e exibe uma mensagem informando que o novo valor de `UserName` é "Worden, Joe".</span><span class="sxs-lookup"><span data-stu-id="25595-141">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25595-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25595-142">See Also</span></span>  
 <span data-ttu-id="25595-143">[Programação orientada a objeto](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span><span class="sxs-lookup"><span data-stu-id="25595-143">[Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2) </span></span>  
<span data-ttu-id="25595-144"> [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="25595-144"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>

