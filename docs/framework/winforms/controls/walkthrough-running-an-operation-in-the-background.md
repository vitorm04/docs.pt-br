---
title: 'Passo a passo: Executando uma operação em segundo plano'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: 6c705c6d6ff9bbd233bbddc3a73acf8aca13a547
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211521"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="20289-102">Passo a passo: Executando uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="20289-102">Walkthrough: Running an Operation in the Background</span></span>

<span data-ttu-id="20289-103">Se você tiver uma operação que levará muito tempo para ser concluída, e você não deseja causar atrasos na interface do usuário, você pode usar o <xref:System.ComponentModel.BackgroundWorker> classe para executar a operação em outro thread.</span><span class="sxs-lookup"><span data-stu-id="20289-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>

<span data-ttu-id="20289-104">Para obter uma listagem completa do código usado neste exemplo, consulte [como: Executar uma operação em segundo plano](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="20289-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>

## <a name="run-an-operation-in-the-background"></a><span data-ttu-id="20289-105">Executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="20289-105">Run an operation in the background</span></span>

1. <span data-ttu-id="20289-106">Com o formulário ativo no Designer de formulários do Windows no Visual Studio, arraste dois <xref:System.Windows.Forms.Button> controles do **caixa de ferramentas** ao formulário e, em seguida, defina as `Name` e <xref:System.Windows.Forms.Control.Text%2A> propriedades dos botões de acordo com o tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="20289-106">With your form active in the Windows Forms Designer in Visual Studio, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>

    |<span data-ttu-id="20289-107">Botão</span><span class="sxs-lookup"><span data-stu-id="20289-107">Button</span></span>|<span data-ttu-id="20289-108">Nome</span><span class="sxs-lookup"><span data-stu-id="20289-108">Name</span></span>|<span data-ttu-id="20289-109">Texto</span><span class="sxs-lookup"><span data-stu-id="20289-109">Text</span></span>|
    |------------|----------|----------|
    |`button1`|`startBtn`|<span data-ttu-id="20289-110">**Iniciar**</span><span class="sxs-lookup"><span data-stu-id="20289-110">**Start**</span></span>|
    |`button2`|`cancelBtn`|<span data-ttu-id="20289-111">**Cancelar**</span><span class="sxs-lookup"><span data-stu-id="20289-111">**Cancel**</span></span>|

2. <span data-ttu-id="20289-112">Abra o **caixa de ferramentas**, clique no **componentes** guia e, em seguida, arraste o <xref:System.ComponentModel.BackgroundWorker> componente para seu formulário.</span><span class="sxs-lookup"><span data-stu-id="20289-112">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>

     <span data-ttu-id="20289-113">O componente `backgroundWorker1` aparece na **Bandeja de Componentes**.</span><span class="sxs-lookup"><span data-stu-id="20289-113">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>

3. <span data-ttu-id="20289-114">No **propriedades** janela, defina as <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="20289-114">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>

4. <span data-ttu-id="20289-115">No **propriedades** janela, clique na **eventos** botão e, em seguida, clique duas vezes o <xref:System.ComponentModel.BackgroundWorker.DoWork> e <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> eventos para criar manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="20289-115">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>

5. <span data-ttu-id="20289-116">Insira seu código demorado no <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="20289-116">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>

6. <span data-ttu-id="20289-117">Extraia os parâmetros necessários para a operação dos <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> propriedade do <xref:System.ComponentModel.DoWorkEventArgs> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="20289-117">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>

7. <span data-ttu-id="20289-118">Atribuir o resultado da computação para o <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> propriedade do <xref:System.ComponentModel.DoWorkEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="20289-118">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>

     <span data-ttu-id="20289-119">Isso será disponibilizado para o <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="20289-119">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]

8. <span data-ttu-id="20289-120">Inserir código para recuperar o resultado de sua operação no <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="20289-120">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]

9. <span data-ttu-id="20289-121">Implementar o método de `TimeConsumingOperation` .</span><span class="sxs-lookup"><span data-stu-id="20289-121">Implement the `TimeConsumingOperation` method.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]

10. <span data-ttu-id="20289-122">No Designer de formulários do Windows, clique duas vezes `startButton` para criar o <xref:System.Windows.Forms.Control.Click> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="20289-122">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

11. <span data-ttu-id="20289-123">Chame o <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método na <xref:System.Windows.Forms.Control.Click> manipulador de eventos para `startButton`.</span><span class="sxs-lookup"><span data-stu-id="20289-123">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]

12. <span data-ttu-id="20289-124">No Designer de formulários do Windows, clique duas vezes `cancelButton` para criar o <xref:System.Windows.Forms.Control.Click> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="20289-124">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>

13. <span data-ttu-id="20289-125">Chame o <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> método na <xref:System.Windows.Forms.Control.Click> manipulador de eventos para `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="20289-125">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]

14. <span data-ttu-id="20289-126">Na parte superior do arquivo, importe os namespaces System.ComponentModel e System.Threading.</span><span class="sxs-lookup"><span data-stu-id="20289-126">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]

15. <span data-ttu-id="20289-127">Pressione **F6** para compilar a solução e, em seguida, pressione **Ctrl**+**F5** para executar o aplicativo fora do depurador.</span><span class="sxs-lookup"><span data-stu-id="20289-127">Press **F6** to build the solution, and then press **Ctrl**+**F5** to run the application outside the debugger.</span></span>

    > [!NOTE]
    > <span data-ttu-id="20289-128">Se você pressionar **F5** para executar o aplicativo no depurador, a exceção gerada no `TimeConsumingOperation` método será capturado e exibido pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="20289-128">If you press **F5** to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="20289-129">Quando você executar o aplicativo fora do depurador, o <xref:System.ComponentModel.BackgroundWorker> manipula a exceção e armazena em cache na <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> propriedade do <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="20289-129">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>

16. <span data-ttu-id="20289-130">Clique no botão **Iniciar** para executar uma operação assíncrona e, em seguida, no botão **Cancelar** para interromper uma operação assíncrona em execução.</span><span class="sxs-lookup"><span data-stu-id="20289-130">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>

     <span data-ttu-id="20289-131">O resultado de cada operação é exibido em um <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="20289-131">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="20289-132">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="20289-132">Next steps</span></span>

- <span data-ttu-id="20289-133">Implemente um formulário que relata o andamento à medida que uma operação assíncrona prossegue.</span><span class="sxs-lookup"><span data-stu-id="20289-133">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="20289-134">Para obter mais informações, confira [Como: Implementar um formulário que usa uma operação em segundo plano](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="20289-134">For more information, see [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>

- <span data-ttu-id="20289-135">Implemente uma classe que dá suporte ao padrão assíncrono para componentes.</span><span class="sxs-lookup"><span data-stu-id="20289-135">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="20289-136">Para obter mais informações, consulte [Implementando o padrão assíncrono baseado em evento](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="20289-136">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="20289-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20289-137">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="20289-138">Como: Implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="20289-138">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="20289-139">Como: Executar uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="20289-139">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="20289-140">Componente BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="20289-140">BackgroundWorker Component</span></span>](backgroundworker-component.md)
