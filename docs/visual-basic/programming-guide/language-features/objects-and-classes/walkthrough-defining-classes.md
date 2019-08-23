---
title: Definindo classes (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 679f4fd55f142c2c4bb63a556feb95c074960b12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914729"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="0e22a-102">Passo a passo: Definindo classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e22a-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="0e22a-103">Este tutorial demonstra como definir classes, que você pode usar para criar objetos.</span><span class="sxs-lookup"><span data-stu-id="0e22a-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="0e22a-104">Ele também mostra como adicionar propriedades e métodos à nova classe e demonstra como inicializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="0e22a-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="0e22a-105">Para definir uma classe</span><span class="sxs-lookup"><span data-stu-id="0e22a-105">To define a class</span></span>
  
1. <span data-ttu-id="0e22a-106">Crie um projeto clicando em **novo projeto** no menu **arquivo** .</span><span class="sxs-lookup"><span data-stu-id="0e22a-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="0e22a-107">A caixa de diálogo **Novo Projeto** é exibida.</span><span class="sxs-lookup"><span data-stu-id="0e22a-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="0e22a-108">Selecione aplicativo do Windows na lista de modelos de projeto Visual Basic para exibir o novo projeto.</span><span class="sxs-lookup"><span data-stu-id="0e22a-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="0e22a-109">Adicione uma nova classe ao projeto clicando em **Adicionar classe** no menu **projeto** .</span><span class="sxs-lookup"><span data-stu-id="0e22a-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="0e22a-110">A caixa de diálogo **Adicionar Novo Item** é exibida.</span><span class="sxs-lookup"><span data-stu-id="0e22a-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="0e22a-111">Selecione o modelo de **classe** .</span><span class="sxs-lookup"><span data-stu-id="0e22a-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="0e22a-112">Nomeie a nova classe `UserNameInfo.vb`e clique em **Adicionar** para exibir o código da nova classe.</span><span class="sxs-lookup"><span data-stu-id="0e22a-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="0e22a-113">Você pode usar o **Editor de código** Visual Basic para adicionar uma classe ao formulário de inicialização digitando `Class` a palavra-chave seguida pelo nome da nova classe.</span><span class="sxs-lookup"><span data-stu-id="0e22a-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="0e22a-114">O **Editor de código** fornece uma `End Class` instrução correspondente para você.</span><span class="sxs-lookup"><span data-stu-id="0e22a-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="0e22a-115">Defina um campo particular para a classe adicionando o seguinte código entre as `Class` instruções e: `End Class`</span><span class="sxs-lookup"><span data-stu-id="0e22a-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="0e22a-116">Declarar o campo como `Private` significa que ele pode ser usado somente dentro da classe.</span><span class="sxs-lookup"><span data-stu-id="0e22a-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="0e22a-117">Você pode disponibilizar os campos de fora de uma classe usando modificadores de acesso `Public` , como o que fornecem mais acesso.</span><span class="sxs-lookup"><span data-stu-id="0e22a-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="0e22a-118">Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0e22a-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="0e22a-119">Defina uma propriedade para a classe adicionando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0e22a-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="0e22a-120">Defina um método para a classe adicionando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0e22a-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="0e22a-121">Defina um construtor com parâmetros para a nova classe adicionando um procedimento chamado `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="0e22a-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="0e22a-122">O `Sub New` Construtor é chamado automaticamente quando um objeto baseado nessa classe é criado.</span><span class="sxs-lookup"><span data-stu-id="0e22a-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="0e22a-123">Esse construtor define o valor do campo que contém o nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="0e22a-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="0e22a-124">Para criar um botão para testar a classe</span><span class="sxs-lookup"><span data-stu-id="0e22a-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="0e22a-125">Altere o formulário de inicialização para o modo de design clicando com o botão direito do mouse em seu nome em **Gerenciador de soluções** e clicando em **Designer de exibição**.</span><span class="sxs-lookup"><span data-stu-id="0e22a-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="0e22a-126">Por padrão, o formulário de inicialização para projetos de aplicativos do Windows é chamado de Form1. vb.</span><span class="sxs-lookup"><span data-stu-id="0e22a-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="0e22a-127">O formulário principal será exibido.</span><span class="sxs-lookup"><span data-stu-id="0e22a-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="0e22a-128">Adicione um botão ao formulário principal e clique duas vezes nele para exibir o código do `Button1_Click` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0e22a-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="0e22a-129">Adicione o seguinte código para chamar o procedimento de teste:</span><span class="sxs-lookup"><span data-stu-id="0e22a-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="0e22a-130">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="0e22a-130">To run your application</span></span>
  
1. <span data-ttu-id="0e22a-131">Execute o aplicativo pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="0e22a-131">Run your application by pressing F5.</span></span> <span data-ttu-id="0e22a-132">Clique no botão no formulário para chamar o procedimento de teste.</span><span class="sxs-lookup"><span data-stu-id="0e22a-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="0e22a-133">Ele exibe uma mensagem informando que `UserName` o original é "Moore, Bobby", pois o procedimento `Capitalize` chamou o método do objeto.</span><span class="sxs-lookup"><span data-stu-id="0e22a-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="0e22a-134">Clique em **OK** para descartar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0e22a-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="0e22a-135">O `Button1 Click` procedimento altera o valor `UserName` da propriedade e exibe uma mensagem informando que o novo valor `UserName` de é "Worden, Joe".</span><span class="sxs-lookup"><span data-stu-id="0e22a-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e22a-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e22a-136">See also</span></span>

- [<span data-ttu-id="0e22a-137">Programação orientada a objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e22a-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="0e22a-138">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="0e22a-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
