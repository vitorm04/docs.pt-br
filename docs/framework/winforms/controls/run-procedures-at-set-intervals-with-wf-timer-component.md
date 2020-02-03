---
title: Executar procedimentos em intervalos definidos com componente de timer
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
ms.openlocfilehash: dcc88beee947e2a83b426dcd2f3fd9d70c20fb67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743116"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Como executar procedimentos em intervalos definidos com o componente de temporizador dos Windows Forms
Às vezes, pode ser útil criar um procedimento que é executado em intervalos de tempo específicos até que um loop termine ou que seja executado quando um determinado período tiver decorrido. O componente <xref:System.Windows.Forms.Timer> torna possível esse procedimento.  
  
 Esse componente foi criado para um ambiente dos Windows Forms. Se você precisar de um temporizador que seja adequado para um ambiente de servidor, consulte [Introdução a temporizadores baseados em servidor](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
> [!NOTE]
> Há algumas limitações ao usar o componente <xref:System.Windows.Forms.Timer>. Para obter mais informações, consulte [Limitações da propriedade de intervalo do componente de temporizador do Windows Forms](limitations-of-the-timer-component-interval-property.md).  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Executar um procedimento em intervalos definidos com o componente Timer  
  
1. Adicione um <xref:System.Windows.Forms.Timer> ao formulário. Consulte a seção Exemplo a seguir para obter ver como fazer isso com programação. O Visual Studio também tem suporte para a adição de componentes a um formulário. Consulte também: [Como adicionar controles sem uma interface do usuário ao Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).  
  
2. Defina a propriedade <xref:System.Windows.Forms.Timer.Interval%2A> (em milissegundos) para o temporizador. Essa propriedade determina quanto tempo passará antes do procedimento ser executado novamente.  
  
    > [!NOTE]
    > Quanto maior a frequência do evento do temporizador, mais tempo do processador é usado em resposta ao evento. Isso pode diminuir o desempenho geral. Não defina um intervalo menor do que o necessário.  
  
3. Escreva o código apropriado no manipulador de eventos <xref:System.Windows.Forms.Timer.Tick>. O código que você escreve nesse evento será executado no intervalo especificado na propriedade <xref:System.Windows.Forms.Timer.Interval%2A>.  
  
4. Defina a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> como `true` para iniciar o temporizador. O evento de <xref:System.Windows.Forms.Timer.Tick> começará a ocorrer, executando o procedimento no intervalo definido.  
  
5. No momento apropriado, defina a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> como `false` para impedir que o procedimento seja executado novamente. Definir o intervalo como `0` não faz o temporizador parar.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Esse primeiro exemplo de código rastreia a hora do dia em incrementos de um segundo. Ele usa um <xref:System.Windows.Forms.Button>, um <xref:System.Windows.Forms.Label>e um componente de <xref:System.Windows.Forms.Timer> em um formulário. A propriedade <xref:System.Windows.Forms.Timer.Interval%2A> é definida como 1000 (igual a um segundo). No evento <xref:System.Windows.Forms.Timer.Tick>, a legenda do rótulo é definida como a hora atual. Quando o botão é clicado, a propriedade <xref:System.Windows.Forms.Timer.Enabled%2A> é definida como `false`, interrompendo o timer de atualizar a legenda do rótulo. O exemplo de código a seguir requer que você tenha um formulário com um controle de <xref:System.Windows.Forms.Button> chamado `Button1`, um controle de <xref:System.Windows.Forms.Timer> chamado `Timer1`e um controle de <xref:System.Windows.Forms.Label> chamado `Label1`.  
  
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
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Este segundo exemplo de código executa um procedimento a cada 600 milissegundos até que um loop seja concluído. O exemplo de código a seguir requer que você tenha um formulário com um controle de <xref:System.Windows.Forms.Button> chamado `Button1`, um controle de <xref:System.Windows.Forms.Timer> chamado `Timer1`e um controle de <xref:System.Windows.Forms.Label> chamado `Label1`.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Timer>
- [Componente Timer](timer-component-windows-forms.md)
- [Visão geral do componente de temporizador](timer-component-overview-windows-forms.md)
