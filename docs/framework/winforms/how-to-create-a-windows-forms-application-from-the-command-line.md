---
title: 'Como: Criar um aplicativo Windows Forms na linha de comando'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c87419a4d730f72a7ee15fcc3127781a8eaff75
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364218"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="423b4-102">Como: Criar um aplicativo Windows Forms na linha de comando</span><span class="sxs-lookup"><span data-stu-id="423b4-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="423b4-103">Os procedimentos a seguir descrevem as etapas básicas que devem ser concluídas para criar e executar um aplicativo do Windows Forms na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="423b4-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="423b4-104">Há um suporte abrangente para esses procedimentos no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="423b4-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="423b4-105">Consulte [também o passo a passos: Hospedagem de um controle de Windows Forms](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)no WPF.</span><span class="sxs-lookup"><span data-stu-id="423b4-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="423b4-106">Procedimento</span><span class="sxs-lookup"><span data-stu-id="423b4-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="423b4-107">Criar o formulário</span><span class="sxs-lookup"><span data-stu-id="423b4-107">To create the form</span></span>  
  
1. <span data-ttu-id="423b4-108">Em um arquivo de código vazio, digite as seguintes instruções de importação ou uso:</span><span class="sxs-lookup"><span data-stu-id="423b4-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="423b4-109">Declare uma classe chamada `Form1` que herda da classe Form.</span><span class="sxs-lookup"><span data-stu-id="423b4-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="423b4-110">Crie um construtor sem parâmetros para `Form1`.</span><span class="sxs-lookup"><span data-stu-id="423b4-110">Create a parameterless constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="423b4-111">Mais código será adicionado ao construtor em um procedimento subsequente.</span><span class="sxs-lookup"><span data-stu-id="423b4-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="423b4-112">Adicione o método `Main` à classe.</span><span class="sxs-lookup"><span data-stu-id="423b4-112">Add a `Main` method to the class.</span></span>  
  
    1. <span data-ttu-id="423b4-113">Aplique o <xref:System.STAThreadAttribute> C# ao método para especificar seu Windows Forms aplicativo é um apartamento de thread único. `Main`</span><span class="sxs-lookup"><span data-stu-id="423b4-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="423b4-114">(O atributo não é necessário em Visual Basic, já que os aplicativos do Windows Forms desenvolvidos com Visual Basic usam um modelo de apartamento de thread único por padrão.)</span><span class="sxs-lookup"><span data-stu-id="423b4-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="423b4-115">Chame <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> para aplicar estilos de sistema operacional ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="423b4-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="423b4-116">Crie uma instância do formulário e execute-o.</span><span class="sxs-lookup"><span data-stu-id="423b4-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="423b4-117">Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="423b4-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="423b4-118">No prompt de comando do .NET Framework, navegue até o diretório em que a classe `Form1` foi criada.</span><span class="sxs-lookup"><span data-stu-id="423b4-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="423b4-119">Compile o formulário.</span><span class="sxs-lookup"><span data-stu-id="423b4-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="423b4-120">Se você estiver usando o C#, digite: `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="423b4-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="423b4-121">Se estiver usando Visual Basic, digite: `vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="423b4-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="423b4-122">No prompt de comando, digite: `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="423b4-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="423b4-123">Adicionando um Controle e Manipulando um Evento</span><span class="sxs-lookup"><span data-stu-id="423b4-123">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="423b4-124">As etapas do procedimento anterior demonstraram como criar um formulário básico do Windows Forms que compila e executa.</span><span class="sxs-lookup"><span data-stu-id="423b4-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="423b4-125">O procedimento a seguir mostra como criar e adicionar um controle ao formulário e manipular um evento para o controle.</span><span class="sxs-lookup"><span data-stu-id="423b4-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="423b4-126">Para obter mais informações sobre os controles que podem ser adicionados a formulários do Windows Forms, consulte [Controles do Windows Forms](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="423b4-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>  
  
 <span data-ttu-id="423b4-127">Além de entender como criar aplicativos do Windows Forms, é necessário compreender a programação baseada em eventos e como tratar a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="423b4-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="423b4-128">Para obter mais informações, consulte [Criando Manipuladores de Eventos no Windows Forms](creating-event-handlers-in-windows-forms.md) e [Tratando a Entrada do Usuário](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="423b4-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="423b4-129">Declarar um controle de botão e manipular o evento de clique</span><span class="sxs-lookup"><span data-stu-id="423b4-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="423b4-130">Declare um controle de botão chamado `button1`.</span><span class="sxs-lookup"><span data-stu-id="423b4-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="423b4-131">No construtor, crie o botão e defina suas <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> Propriedades e <xref:System.Windows.Forms.Control.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="423b4-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="423b4-132">Adicione o botão ao formulário.</span><span class="sxs-lookup"><span data-stu-id="423b4-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="423b4-133">O exemplo de código a seguir demonstra como declarar o controle de botão.</span><span class="sxs-lookup"><span data-stu-id="423b4-133">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="423b4-134">Crie um método para manipular o <xref:System.Windows.Forms.Control.Click> evento para o botão.</span><span class="sxs-lookup"><span data-stu-id="423b4-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="423b4-135">No manipulador de eventos de clique, exiba <xref:System.Windows.Forms.MessageBox> um com a mensagem "Olá, mundo".</span><span class="sxs-lookup"><span data-stu-id="423b4-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="423b4-136">O exemplo de código a seguir demonstra como manipular o evento de clique do controle de botão.</span><span class="sxs-lookup"><span data-stu-id="423b4-136">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="423b4-137">Associe o <xref:System.Windows.Forms.Control.Click> evento ao método que você criou.</span><span class="sxs-lookup"><span data-stu-id="423b4-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="423b4-138">O exemplo de código a seguir demonstra como associar o evento ao método.</span><span class="sxs-lookup"><span data-stu-id="423b4-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="423b4-139">Compile e execute o aplicativo, conforme descrito no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="423b4-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="423b4-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="423b4-140">Example</span></span>  
 <span data-ttu-id="423b4-141">O exemplo de código a seguir é o exemplo completo dos procedimentos anteriores.</span><span class="sxs-lookup"><span data-stu-id="423b4-141">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="423b4-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="423b4-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="423b4-143">Alterando a aparência dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="423b4-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="423b4-144">Aprimorando aplicativos do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="423b4-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="423b4-145">Guia de introdução ao Windows Forms</span><span class="sxs-lookup"><span data-stu-id="423b4-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
