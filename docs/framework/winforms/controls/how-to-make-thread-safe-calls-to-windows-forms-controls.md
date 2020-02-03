---
title: Fazer chamadas thread-safe para controles
ms.date: 02/19/2019
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: 101457ab2a02b8de49d06c354ca307e07b690ba2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736156"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Como: fazer chamadas de thread-safe para Windows Forms controles

O multithreading pode melhorar o desempenho de aplicativos Windows Forms, mas o acesso aos controles Windows Forms não é inerentemente seguro ao thread. O multithreading pode expor seu código a bugs muito graves e complexos. Dois ou mais threads manipulando um controle podem forçar o controle em um estado inconsistente e levar a condições de corrida, deadlocks e congelamento ou travamentos. Se você implementar multithreading em seu aplicativo, certifique-se de chamar controles entre threads de forma segura para thread. Para obter mais informações, consulte [práticas recomendadas de Threading gerenciadas](../../../standard/threading/managed-threading-best-practices.md). 

Há duas maneiras de chamar com segurança um controle de Windows Forms de um thread que não criou esse controle. Você pode usar o método <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> para chamar um delegado criado no thread principal que, por sua vez, chama o controle. Ou, você pode implementar um <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, que usa um modelo controlado por eventos para separar o trabalho feito no thread em segundo plano de relatórios sobre os resultados. 

## <a name="unsafe-cross-thread-calls"></a>Chamadas de thread cruzado não seguras

Não é seguro chamar um controle diretamente de um thread que não o criou. O trecho de código a seguir ilustra uma chamada não segura para o controle <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>. O manipulador de eventos `Button1_Click` cria um novo thread de `WriteTextUnsafe`, que define a propriedade <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> do thread principal diretamente. 

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

O depurador do Visual Studio detecta essas chamadas de thread não seguras gerando um <xref:System.InvalidOperationException> com a mensagem, **operação entre threads não é válida. Controle "" acessado de um thread que não seja o thread em que foi criado.** O <xref:System.InvalidOperationException> sempre ocorre para chamadas de thread cruzado não seguras durante a depuração do Visual Studio e pode ocorrer no tempo de execução do aplicativo. Você deve corrigir o problema, mas pode desabilitar a exceção definindo a propriedade <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> como `false`.

## <a name="safe-cross-thread-calls"></a>Chamadas de thread cruzado seguras 

Os exemplos de código a seguir demonstram duas maneiras de chamar com segurança um controle de Windows Forms de um thread que não o criou: 

1. O método <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>, que chama um delegado do thread principal para chamar o controle. 
2. Um componente <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, que oferece um modelo controlado por evento. 

Em ambos os exemplos, o thread em segundo plano é suspenso por um segundo para simular o trabalho que está sendo feito nesse thread. 

Você pode criar e executar esses exemplos como .NET Framework aplicativos da linha C# de comando ou Visual Basic. Para obter mais informações, consulte [criação de linha de comando com CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [Build na linha de comando (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

A partir do .NET Core 3,0, você também pode criar e executar os exemplos como aplicativos do Windows .NET Core a partir de uma pasta que tenha um .NET Core Windows Forms *\<nome da pasta >* arquivo de projeto. csproj. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Exemplo: usar o método Invoke com um delegate

O exemplo a seguir demonstra um padrão para garantir chamadas de thread-safe para um controle Windows Forms. Ele consulta a propriedade <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>, que compara a ID de thread de criação do controle com a ID de thread de chamada. Se as IDs de thread forem as mesmas, ele chamará o controle diretamente. Se as IDs de thread forem diferentes, ele chamará o método <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> com um delegado do thread principal, que faz a chamada real para o controle.

O `SafeCallDelegate` permite definir a propriedade <xref:System.Windows.Forms.TextBox.Text%2A> do controle de <xref:System.Windows.Forms.TextBox>. O método `WriteTextSafe` consulta <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Se <xref:System.Windows.Forms.Control.InvokeRequired%2A> retornar `true`, `WriteTextSafe` passará o `SafeCallDelegate` para o método <xref:System.Windows.Forms.Control.Invoke%2A> para fazer a chamada real para o controle. Se <xref:System.Windows.Forms.Control.InvokeRequired%2A> retornar `false`, `WriteTextSafe` definirá o <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> diretamente. O manipulador de eventos `Button1_Click` cria o novo thread e executa o método `WriteTextSafe`. 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Exemplo: usar um manipulador de eventos de BackgroundWorker

Uma maneira fácil de implementar multithreading é com o componente <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, que usa um modelo controlado por eventos. O thread em segundo plano executa o evento <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>, que não interage com o thread principal. O thread principal executa o <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> e <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> manipuladores de eventos, que podem chamar os controles do thread principal.

Para fazer uma chamada thread-safe usando <xref:System.ComponentModel.BackgroundWorker>, crie um método no thread em segundo plano para fazer o trabalho e associá-lo ao evento <xref:System.ComponentModel.BackgroundWorker.DoWork>. Crie outro método no thread principal para relatar os resultados do trabalho em segundo plano e associá-los ao evento <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> ou <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>. Para iniciar o thread em segundo plano, chame <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>. 

O exemplo usa o manipulador de eventos <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> para definir a propriedade <xref:System.Windows.Forms.TextBox.Text%2A> do controle de <xref:System.Windows.Forms.TextBox>. Para obter um exemplo usando o evento <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, consulte <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.BackgroundWorker>
- [Como executar uma operação em segundo plano](how-to-run-an-operation-in-the-background.md)
- [Como: implementar um formulário que usa uma operação em segundo plano](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Desenvolva controles de Windows Forms personalizados com o .NET Framework](developing-custom-windows-forms-controls.md)
