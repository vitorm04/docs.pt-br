---
title: 'Passo a passo: Atualizando informações da barra de status em tempo de execução'
ms.date: 03/30/2017
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
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930981"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="2ac75-102">Passo a passo: Atualizando informações da barra de status em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="2ac75-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
> <span data-ttu-id="2ac75-103">Os <xref:System.Windows.Forms.StatusStrip> controles <xref:System.Windows.Forms.ToolStripStatusLabel> e <xref:System.Windows.Forms.StatusBar> substituem e adicionam funcionalidade aos <xref:System.Windows.Forms.StatusBarPanel> controles e; no entanto <xref:System.Windows.Forms.StatusBarPanel> , os <xref:System.Windows.Forms.StatusBar> controles e são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolha.</span><span class="sxs-lookup"><span data-stu-id="2ac75-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="2ac75-104">Geralmente, um programa solicitará que você atualize o conteúdo dos painéis da barra de status dinamicamente no tempo de execução, dependendo das alterações de estado do aplicativo ou outra interação do usuário.</span><span class="sxs-lookup"><span data-stu-id="2ac75-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="2ac75-105">Essa é uma maneira comum de indicar aos usuários que teclas como CAPS LOCK, NUM LOCK ou SCROLL LOCK estão habilitadas ou de fornecer uma data ou um relógio como uma referência conveniente.</span><span class="sxs-lookup"><span data-stu-id="2ac75-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="2ac75-106">No exemplo a seguir, você usará uma instância da <xref:System.Windows.Forms.StatusBarPanel> classe para hospedar um relógio.</span><span class="sxs-lookup"><span data-stu-id="2ac75-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="2ac75-107">Preparar a barra de status para atualização</span><span class="sxs-lookup"><span data-stu-id="2ac75-107">To get the status bar ready for updating</span></span>  
  
1. <span data-ttu-id="2ac75-108">Crie um novo formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="2ac75-108">Create a new Windows form.</span></span>  
  
2. <span data-ttu-id="2ac75-109">Adicione um controle <xref:System.Windows.Forms.StatusBar> ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="2ac75-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="2ac75-110">Para obter detalhes, confira [Como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2ac75-110">For details, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="2ac75-111">Adicione um painel da barra de status <xref:System.Windows.Forms.StatusBar> ao seu controle.</span><span class="sxs-lookup"><span data-stu-id="2ac75-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="2ac75-112">Para obter detalhes, confira [Como: Adicione painéis a um controle](how-to-add-panels-to-a-statusbar-control.md)StatusBar.</span><span class="sxs-lookup"><span data-stu-id="2ac75-112">For details, see [How to: Add Panels to a StatusBar Control](how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4. <span data-ttu-id="2ac75-113">Para o <xref:System.Windows.Forms.StatusBar> controle adicionado ao formulário, defina a <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> Propriedade como `true`.</span><span class="sxs-lookup"><span data-stu-id="2ac75-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5. <span data-ttu-id="2ac75-114">Adicione um componente <xref:System.Windows.Forms.Timer> Windows Forms ao formulário.</span><span class="sxs-lookup"><span data-stu-id="2ac75-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2ac75-115">O componente <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Windows Forms é projetado para um ambiente de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ac75-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="2ac75-116">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2ac75-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
6. <span data-ttu-id="2ac75-117">Defina a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> como `true`.</span><span class="sxs-lookup"><span data-stu-id="2ac75-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7. <span data-ttu-id="2ac75-118">Defina a <xref:System.Windows.Forms.Timer.Interval%2A> propriedade <xref:System.Windows.Forms.Timer> de como 30000.</span><span class="sxs-lookup"><span data-stu-id="2ac75-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2ac75-119">A <xref:System.Windows.Forms.Timer.Interval%2A> propriedade<xref:System.Windows.Forms.Timer> do componente é definida como 30 segundos (30.000 milissegundos) para garantir que um tempo preciso seja refletido no tempo exibido.</span><span class="sxs-lookup"><span data-stu-id="2ac75-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="2ac75-120">Implementar o temporizador para atualizar a barra de status</span><span class="sxs-lookup"><span data-stu-id="2ac75-120">To implement the timer to update the status bar</span></span>  
  
1. <span data-ttu-id="2ac75-121">Insira o código a seguir no manipulador de eventos do <xref:System.Windows.Forms.Timer> componente para atualizar o painel <xref:System.Windows.Forms.StatusBar> do controle.</span><span class="sxs-lookup"><span data-stu-id="2ac75-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
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
  
     <span data-ttu-id="2ac75-122">Neste ponto, você está pronto para executar o aplicativo e observar o relógio em execução no painel da barra de status.</span><span class="sxs-lookup"><span data-stu-id="2ac75-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="2ac75-123">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="2ac75-123">To test the application</span></span>  
  
1. <span data-ttu-id="2ac75-124">Depure o aplicativo e pressione F5 para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ac75-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="2ac75-125">Para ver mais detalhes sobre depuração, consulte [Depuração no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2ac75-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2ac75-126">Levará cerca de 30 segundos para o relógio aparecer na barra de status.</span><span class="sxs-lookup"><span data-stu-id="2ac75-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="2ac75-127">Isso serve para obter a hora mais precisa possível.</span><span class="sxs-lookup"><span data-stu-id="2ac75-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="2ac75-128">Por outro lado, para que o relógio apareça mais cedo, você pode reduzir o valor da <xref:System.Windows.Forms.Timer.Interval%2A> propriedade definida na etapa 7 no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="2ac75-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac75-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ac75-129">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="2ac75-130">Como: Adicionar painéis a um controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="2ac75-130">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)
- [<span data-ttu-id="2ac75-131">Como: Determine em qual painel no controle StatusBar Windows Forms foi clicado</span><span class="sxs-lookup"><span data-stu-id="2ac75-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="2ac75-132">Visão geral do controle StatusBar</span><span class="sxs-lookup"><span data-stu-id="2ac75-132">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
