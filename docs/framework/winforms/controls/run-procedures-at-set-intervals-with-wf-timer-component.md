---
title: Como executar procedimentos em intervalos definidos com o componente de temporizador dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: bf0e22eab3b6517521dbe06a73f63af232746df1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45528997"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a><span data-ttu-id="86c72-102">Como executar procedimentos em intervalos definidos com o componente de temporizador dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86c72-102">How to: Run Procedures at Set Intervals with the Windows Forms Timer Component</span></span>
<span data-ttu-id="86c72-103">Às vezes, pode ser útil criar um procedimento que é executado em intervalos de tempo específicos até que um loop termine ou que seja executado quando um determinado período tiver decorrido.</span><span class="sxs-lookup"><span data-stu-id="86c72-103">You might sometimes want to create a procedure that runs at specific time intervals until a loop has finished or that runs when a set time interval has elapsed.</span></span> <span data-ttu-id="86c72-104">O <xref:System.Windows.Forms.Timer> componente possibilita tal procedimento.</span><span class="sxs-lookup"><span data-stu-id="86c72-104">The <xref:System.Windows.Forms.Timer> component makes such a procedure possible.</span></span>  
  
 <span data-ttu-id="86c72-105">Esse componente foi projetado para um ambiente do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="86c72-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="86c72-106">Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="86c72-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86c72-107">Há algumas limitações ao usar o <xref:System.Windows.Forms.Timer> componente.</span><span class="sxs-lookup"><span data-stu-id="86c72-107">There are some limitations when using the <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="86c72-108">Para obter mais informações, consulte [Limitações da propriedade de intervalo do componente de temporizador do Windows Forms](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span><span class="sxs-lookup"><span data-stu-id="86c72-108">For more information, see [Limitations of the Windows Forms Timer Component's Interval Property](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).</span></span>  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a><span data-ttu-id="86c72-109">Executar um procedimento em intervalos definidos com o componente Timer</span><span class="sxs-lookup"><span data-stu-id="86c72-109">To run a procedure at set intervals with the Timer component</span></span>  
  
1.  <span data-ttu-id="86c72-110">Adicionar um <xref:System.Windows.Forms.Timer> ao seu formulário.</span><span class="sxs-lookup"><span data-stu-id="86c72-110">Add a <xref:System.Windows.Forms.Timer> to your form.</span></span> <span data-ttu-id="86c72-111">Consulte a seção Exemplo a seguir para obter ver como fazer isso com programação.</span><span class="sxs-lookup"><span data-stu-id="86c72-111">See the following Example section for an illustration of how to do this programmatically.</span></span> <span data-ttu-id="86c72-112">Visual Studio também tem suporte para adicionar componentes a um formulário.</span><span class="sxs-lookup"><span data-stu-id="86c72-112">Visual Studio also has support for adding components to a form.</span></span> <span data-ttu-id="86c72-113">Consulte também: [Como adicionar controles sem uma interface do usuário ao Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="86c72-113">Also see [How to: Add Controls Without a User Interface to Windows Forms](https://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).</span></span>  
  
2.  <span data-ttu-id="86c72-114">Defina o <xref:System.Windows.Forms.Timer.Interval%2A> propriedade (em milissegundos) para o temporizador.</span><span class="sxs-lookup"><span data-stu-id="86c72-114">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property (in milliseconds) for the timer.</span></span> <span data-ttu-id="86c72-115">Essa propriedade determina quanto tempo passará antes do procedimento ser executado novamente.</span><span class="sxs-lookup"><span data-stu-id="86c72-115">This property determines how much time will pass before the procedure is run again.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86c72-116">Quanto maior a frequência do evento do temporizador, mais tempo do processador é usado em resposta ao evento.</span><span class="sxs-lookup"><span data-stu-id="86c72-116">The more often a timer event occurs, the more processor time is used in responding to the event.</span></span> <span data-ttu-id="86c72-117">Isso pode diminuir o desempenho geral.</span><span class="sxs-lookup"><span data-stu-id="86c72-117">This can slow down overall performance.</span></span> <span data-ttu-id="86c72-118">Não defina um intervalo menor do que o necessário.</span><span class="sxs-lookup"><span data-stu-id="86c72-118">Do not set a smaller interval than you need.</span></span>  
  
3.  <span data-ttu-id="86c72-119">Escreva o código apropriado <xref:System.Windows.Forms.Timer.Tick> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="86c72-119">Write appropriate code in the <xref:System.Windows.Forms.Timer.Tick> event handler.</span></span> <span data-ttu-id="86c72-120">O código que você escreve neste evento será executado no intervalo especificado na <xref:System.Windows.Forms.Timer.Interval%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="86c72-120">The code you write in this event will run at the interval specified in the <xref:System.Windows.Forms.Timer.Interval%2A> property.</span></span>  
  
4.  <span data-ttu-id="86c72-121">Defina as <xref:System.Windows.Forms.Timer.Enabled%2A> propriedade para `true` para iniciar o temporizador.</span><span class="sxs-lookup"><span data-stu-id="86c72-121">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true` to start the timer.</span></span> <span data-ttu-id="86c72-122">O <xref:System.Windows.Forms.Timer.Tick> evento começará a ocorrer, executando o procedimento no intervalo definido.</span><span class="sxs-lookup"><span data-stu-id="86c72-122">The <xref:System.Windows.Forms.Timer.Tick> event will begin to occur, running your procedure at the set interval.</span></span>  
  
5.  <span data-ttu-id="86c72-123">No momento apropriado, defina as <xref:System.Windows.Forms.Timer.Enabled%2A> propriedade para `false` para impedir que o procedimento seja executado novamente.</span><span class="sxs-lookup"><span data-stu-id="86c72-123">At the appropriate time, set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `false` to stop the procedure from running again.</span></span> <span data-ttu-id="86c72-124">Definir o intervalo como `0` não faz o temporizador parar.</span><span class="sxs-lookup"><span data-stu-id="86c72-124">Setting the interval to `0` does not cause the timer to stop.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86c72-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86c72-125">Example</span></span>  
 <span data-ttu-id="86c72-126">Esse primeiro exemplo de código rastreia a hora do dia em incrementos de um segundo.</span><span class="sxs-lookup"><span data-stu-id="86c72-126">This first code example tracks the time of day in one-second increments.</span></span> <span data-ttu-id="86c72-127">Ele usa um <xref:System.Windows.Forms.Button>, um <xref:System.Windows.Forms.Label>e um <xref:System.Windows.Forms.Timer> componente em um formulário.</span><span class="sxs-lookup"><span data-stu-id="86c72-127">It uses a <xref:System.Windows.Forms.Button>, a <xref:System.Windows.Forms.Label>, and a <xref:System.Windows.Forms.Timer> component on a form.</span></span> <span data-ttu-id="86c72-128">O <xref:System.Windows.Forms.Timer.Interval%2A> estiver definida como 1000 (igual a um segundo).</span><span class="sxs-lookup"><span data-stu-id="86c72-128">The <xref:System.Windows.Forms.Timer.Interval%2A> property is set to 1000 (equal to one second).</span></span> <span data-ttu-id="86c72-129">No <xref:System.Windows.Forms.Timer.Tick> evento, a legenda do rótulo é definida para a hora atual.</span><span class="sxs-lookup"><span data-stu-id="86c72-129">In the <xref:System.Windows.Forms.Timer.Tick> event, the label's caption is set to the current time.</span></span> <span data-ttu-id="86c72-130">Quando o botão é clicado, o <xref:System.Windows.Forms.Timer.Enabled%2A> estiver definida como `false`, interrompendo o timer de atualização de legenda do rótulo.</span><span class="sxs-lookup"><span data-stu-id="86c72-130">When the button is clicked, the <xref:System.Windows.Forms.Timer.Enabled%2A> property is set to `false`, stopping the timer from updating the label's caption.</span></span> <span data-ttu-id="86c72-131">O exemplo de código a seguir exige que você tenha um formulário com um <xref:System.Windows.Forms.Button> controle chamado `Button1`, um <xref:System.Windows.Forms.Timer> controle denominado `Timer1`e um <xref:System.Windows.Forms.Label> controle chamado `Label1`.</span><span class="sxs-lookup"><span data-stu-id="86c72-131">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a><span data-ttu-id="86c72-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86c72-132">Example</span></span>  
 <span data-ttu-id="86c72-133">Este segundo exemplo de código executa um procedimento a cada 600 milissegundos até que um loop seja concluído.</span><span class="sxs-lookup"><span data-stu-id="86c72-133">This second code example runs a procedure every 600 milliseconds until a loop has finished.</span></span> <span data-ttu-id="86c72-134">O exemplo de código a seguir exige que você tenha um formulário com um <xref:System.Windows.Forms.Button> controle chamado `Button1`, um <xref:System.Windows.Forms.Timer> controle denominado `Timer1`e um <xref:System.Windows.Forms.Label> controle chamado `Label1`.</span><span class="sxs-lookup"><span data-stu-id="86c72-134">The following code example requires that you have a form with a <xref:System.Windows.Forms.Button> control named `Button1`, a <xref:System.Windows.Forms.Timer> control named `Timer1`, and a <xref:System.Windows.Forms.Label> control named `Label1`.</span></span>  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="86c72-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86c72-135">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="86c72-136">Componente Timer</span><span class="sxs-lookup"><span data-stu-id="86c72-136">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="86c72-137">Visão geral do componente de temporizador</span><span class="sxs-lookup"><span data-stu-id="86c72-137">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
