---
title: 'Como: criar um aplicativo Windows Forms a partir da linha de comando'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6ddb27f724e30071be339ac753cfd85599ccd86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="e40f3-102">Como: criar um aplicativo Windows Forms a partir da linha de comando</span><span class="sxs-lookup"><span data-stu-id="e40f3-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="e40f3-103">Os procedimentos a seguir descrevem as etapas básicas que devem ser concluídas para criar e executar um aplicativo do Windows Forms na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e40f3-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="e40f3-104">Há um suporte abrangente para esses procedimentos no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e40f3-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="e40f3-105">Consulte também as [Instruções Passo a Passo: Criando um Formulários Simples do Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span><span class="sxs-lookup"><span data-stu-id="e40f3-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e40f3-106">Procedimento</span><span class="sxs-lookup"><span data-stu-id="e40f3-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="e40f3-107">Criar o formulário</span><span class="sxs-lookup"><span data-stu-id="e40f3-107">To create the form</span></span>  
  
1.  <span data-ttu-id="e40f3-108">Em um arquivo de código vazio, digite as seguintes instruções de importação ou uso:</span><span class="sxs-lookup"><span data-stu-id="e40f3-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="e40f3-109">Declare uma classe chamada `Form1` que herda da classe Form.</span><span class="sxs-lookup"><span data-stu-id="e40f3-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="e40f3-110">Crie um construtor padrão para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="e40f3-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="e40f3-111">Mais código será adicionado ao construtor em um procedimento subsequente.</span><span class="sxs-lookup"><span data-stu-id="e40f3-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="e40f3-112">Adicione o método `Main` à classe.</span><span class="sxs-lookup"><span data-stu-id="e40f3-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="e40f3-113">Aplicar o <xref:System.STAThreadAttribute> para o `Main` método para especificar o aplicativo de formulários do Windows é um compartimento de thread único.</span><span class="sxs-lookup"><span data-stu-id="e40f3-113">Apply the <xref:System.STAThreadAttribute> to the `Main` method to specify your Windows Forms application is a single threaded apartment.</span></span>  
  
    2.  <span data-ttu-id="e40f3-114">Chamar <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> para dar uma aparência do Windows XP para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e40f3-114">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to give a Windows XP appearance to your application.</span></span>  
  
    3.  <span data-ttu-id="e40f3-115">Crie uma instância do formulário e execute-o.</span><span class="sxs-lookup"><span data-stu-id="e40f3-115">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="e40f3-116">Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="e40f3-116">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="e40f3-117">No prompt de comando do .NET Framework, navegue até o diretório em que a classe `Form1` foi criada.</span><span class="sxs-lookup"><span data-stu-id="e40f3-117">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="e40f3-118">Compile o formulário.</span><span class="sxs-lookup"><span data-stu-id="e40f3-118">Compile the form.</span></span>  
  
    -   <span data-ttu-id="e40f3-119">Se você estiver usando o C#, digite: `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="e40f3-119">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="e40f3-120">Se estiver usando Visual Basic, digite: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span><span class="sxs-lookup"><span data-stu-id="e40f3-120">If you are using Visual Basic, type: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span></span>  
  
3.  <span data-ttu-id="e40f3-121">No prompt de comando, digite: `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="e40f3-121">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="e40f3-122">Adicionando um Controle e Manipulando um Evento</span><span class="sxs-lookup"><span data-stu-id="e40f3-122">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="e40f3-123">As etapas do procedimento anterior demonstraram como criar um formulário básico do Windows Forms que compila e executa.</span><span class="sxs-lookup"><span data-stu-id="e40f3-123">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="e40f3-124">O procedimento a seguir mostra como criar e adicionar um controle ao formulário e manipular um evento para o controle.</span><span class="sxs-lookup"><span data-stu-id="e40f3-124">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="e40f3-125">Para obter mais informações sobre os controles que podem ser adicionados a formulários do Windows Forms, consulte [Controles do Windows Forms](../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="e40f3-125">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="e40f3-126">Além de entender como criar aplicativos do Windows Forms, é necessário compreender a programação baseada em eventos e como tratar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="e40f3-126">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="e40f3-127">Para obter mais informações, consulte [Criando Manipuladores de Eventos no Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md) e [Tratando a Entrada do Usuário](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="e40f3-127">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="e40f3-128">Declarar um controle de botão e manipular o evento de clique</span><span class="sxs-lookup"><span data-stu-id="e40f3-128">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="e40f3-129">Declare um controle de botão chamado `button1`.</span><span class="sxs-lookup"><span data-stu-id="e40f3-129">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="e40f3-130">No construtor, crie o botão e defina seu <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> e <xref:System.Windows.Forms.Control.Text%2A> propriedades.</span><span class="sxs-lookup"><span data-stu-id="e40f3-130">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="e40f3-131">Adicione o botão ao formulário.</span><span class="sxs-lookup"><span data-stu-id="e40f3-131">Add the button to the form.</span></span>  
  
     <span data-ttu-id="e40f3-132">O exemplo de código a seguir demonstra como declarar o controle de botão.</span><span class="sxs-lookup"><span data-stu-id="e40f3-132">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="e40f3-133">Criar um método para tratar o <xref:System.Windows.Forms.Control.Click> eventos do botão.</span><span class="sxs-lookup"><span data-stu-id="e40f3-133">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="e40f3-134">No manipulador de eventos de clique, exiba um <xref:System.Windows.Forms.MessageBox> com a mensagem "Hello World".</span><span class="sxs-lookup"><span data-stu-id="e40f3-134">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="e40f3-135">O exemplo de código a seguir demonstra como manipular o evento de clique do controle de botão.</span><span class="sxs-lookup"><span data-stu-id="e40f3-135">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="e40f3-136">Associar o <xref:System.Windows.Forms.Control.Click> evento com o método que você criou.</span><span class="sxs-lookup"><span data-stu-id="e40f3-136">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="e40f3-137">O exemplo de código a seguir demonstra como associar o evento ao método.</span><span class="sxs-lookup"><span data-stu-id="e40f3-137">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="e40f3-138">Compile e execute o aplicativo, conforme descrito no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="e40f3-138">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e40f3-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e40f3-139">Example</span></span>  
 <span data-ttu-id="e40f3-140">O exemplo de código a seguir é o exemplo completo dos procedimentos anteriores.</span><span class="sxs-lookup"><span data-stu-id="e40f3-140">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e40f3-141">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e40f3-141">Compiling the Code</span></span>  
  
-   <span data-ttu-id="e40f3-142">Para compilar o código, siga as instruções no procedimento a seguir que descrevem como compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e40f3-142">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40f3-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e40f3-143">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="e40f3-144">Alterando a aparência dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e40f3-144">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="e40f3-145">Aprimorando aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e40f3-145">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="e40f3-146">Introdução ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e40f3-146">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
