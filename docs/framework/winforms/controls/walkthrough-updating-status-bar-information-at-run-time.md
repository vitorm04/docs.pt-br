---
title: "Instruções passo a passo: atualizando informações da barra de status em tempo de execução"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96b9c0caeecd4ae381ff2d163e9bf9ff0a89538f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="d58d6-102">Instruções passo a passo: atualizando informações da barra de status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d58d6-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="d58d6-103">O <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> controles substituir e adiciona a funcionalidade para o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controla; no entanto, o <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> controles são mantidos para compatibilidade com versões anteriores e o uso futuro, se você Escolha.</span><span class="sxs-lookup"><span data-stu-id="d58d6-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d58d6-104">Geralmente, um programa solicitará que você atualize o conteúdo dos painéis da barra de status dinamicamente no tempo de execução, dependendo das alterações de estado do aplicativo ou outra interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="d58d6-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="d58d6-105">Essa é uma maneira comum de indicar aos usuários que teclas como CAPS LOCK, NUM LOCK ou SCROLL LOCK estão habilitadas ou de fornecer uma data ou um relógio como uma referência conveniente.</span><span class="sxs-lookup"><span data-stu-id="d58d6-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="d58d6-106">O exemplo a seguir, você usará uma instância do <xref:System.Windows.Forms.StatusBarPanel> classe para hospedar um relógio.</span><span class="sxs-lookup"><span data-stu-id="d58d6-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="d58d6-107">Preparar a barra de status para atualização</span><span class="sxs-lookup"><span data-stu-id="d58d6-107">To get the status bar ready for updating</span></span>  
  
1.  <span data-ttu-id="d58d6-108">Crie um novo formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="d58d6-108">Create a new Windows form.</span></span>  
  
2.  <span data-ttu-id="d58d6-109">Adicione um controle <xref:System.Windows.Forms.StatusBar> ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="d58d6-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="d58d6-110">Para ver mais detalhes, consulte [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d58d6-110">For details, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="d58d6-111">Adicionar um painel da barra de status para o <xref:System.Windows.Forms.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="d58d6-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="d58d6-112">Para ver mais detalhes, consulte [Como adicionar painéis a um controle StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="d58d6-112">For details, see [How to: Add Panels to a StatusBar Control](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4.  <span data-ttu-id="d58d6-113">Para o <xref:System.Windows.Forms.StatusBar> controle adicionado ao formulário, defina o <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="d58d6-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="d58d6-114">Adicione um Windows Forms <xref:System.Windows.Forms.Timer> componente para o formulário.</span><span class="sxs-lookup"><span data-stu-id="d58d6-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d58d6-115">Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> componente é criado para um ambiente de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d58d6-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="d58d6-116">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="d58d6-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
6.  <span data-ttu-id="d58d6-117">Defina a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="d58d6-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7.  <span data-ttu-id="d58d6-118">Definir o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade o <xref:System.Windows.Forms.Timer> como 30000.</span><span class="sxs-lookup"><span data-stu-id="d58d6-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d58d6-119">O <xref:System.Windows.Forms.Timer.Interval%2A> propriedade o <xref:System.Windows.Forms.Timer> componente é definido como 30 segundos (30.000 milissegundos) para garantir que precisa do tempo é refletida no horário exibido.</span><span class="sxs-lookup"><span data-stu-id="d58d6-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="d58d6-120">Implementar o temporizador para atualizar a barra de status</span><span class="sxs-lookup"><span data-stu-id="d58d6-120">To implement the timer to update the status bar</span></span>  
  
1.  <span data-ttu-id="d58d6-121">Insira o seguinte código no manipulador de eventos do <xref:System.Windows.Forms.Timer> componente para atualizar o painel do <xref:System.Windows.Forms.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="d58d6-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     <span data-ttu-id="d58d6-122">Neste ponto, você está pronto para executar o aplicativo e observar o relógio em execução no painel da barra de status.</span><span class="sxs-lookup"><span data-stu-id="d58d6-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="d58d6-123">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="d58d6-123">To test the application</span></span>  
  
1.  <span data-ttu-id="d58d6-124">Depure o aplicativo e pressione F5 para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="d58d6-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="d58d6-125">Para ver mais detalhes sobre depuração, consulte [Depuração no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d58d6-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d58d6-126">Levará cerca de 30 segundos para o relógio aparecer na barra de status.</span><span class="sxs-lookup"><span data-stu-id="d58d6-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="d58d6-127">Isso serve para obter a hora mais precisa possível.</span><span class="sxs-lookup"><span data-stu-id="d58d6-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="d58d6-128">Por outro lado, para fazer com que o relógio apareça antes, você pode reduzir o valor de <xref:System.Windows.Forms.Timer.Interval%2A> propriedade definida na etapa 7 no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="d58d6-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58d6-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d58d6-129">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="d58d6-130">Como adicionar painéis a um controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="d58d6-130">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [<span data-ttu-id="d58d6-131">Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="d58d6-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="d58d6-132">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="d58d6-132">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
