---
title: 'Como: Fazer chamadas thread-safe para controles dos Windows Forms'
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
ms.openlocfilehash: ef7836721df6c090a4d09c38c176641331c3e8a4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362559"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Como: Fazer chamadas thread-safe para controles dos Windows Forms

O multithreading pode melhorar o desempenho de aplicativos do Windows Forms, mas o acesso aos controles de formulários do Windows não é inerentemente thread-safe. O multithreading pode expor seu código a bugs muito sérios e complexos. Dois ou mais threads manipulando um controle podem forçar o controle em um estado inconsistente e levar a condições de corrida, deadlocks e congelamentos ou travamentos. Se você implementar multithreading em seu aplicativo, certifique-se de chamar os controles de thread cruzado de forma thread-safe. Para obter mais informações, consulte [práticas recomendadas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md). 

Há duas maneiras de chamar com segurança um controle dos Windows Forms de um thread que não tiver criado esse controle. Você pode usar o <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> método para chamar um delegado que foi criado no thread principal, que por sua vez chama o controle. Ou, você pode implementar um <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, que usa um modelo controlado por evento para separar o trabalho realizado no thread de segundo plano de relatar os resultados. 

## <a name="unsafe-cross-thread-calls"></a>Chamadas de thread cruzado não seguras

Não é seguro chamar um controle diretamente a partir de um thread que não a tenha criado. O trecho de código a seguir ilustra uma chamada não segura para o <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> controle. O `Button1_Click` manipulador de eventos cria um novo `WriteTextUnsafe` thread, que define o thread principal <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> propriedade diretamente. 

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

O depurador do Visual Studio detecta essas chamadas do thread não seguro, gerando um <xref:System.InvalidOperationException> com a mensagem **operação de thread cruzado não é válida. Controle de "" acessado de um thread diferente do thread que foi criado.** O <xref:System.InvalidOperationException> sempre ocorre para chamadas de thread cruzado não seguras durante a depuração do Visual Studio e podem ocorrer em tempo de execução do aplicativo. Você deve corrigir o problema, mas você pode desativar a exceção, definindo o <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> propriedade para `false`.

## <a name="safe-cross-thread-calls"></a>Chamadas seguras de thread cruzado 

Os exemplos de código a seguir demonstram duas maneiras de chamar com segurança um controle dos Windows Forms de um thread que não a tenha criado: 
1. O <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> método, que chama um delegado do thread principal para o controle de chamada. 
2. Um <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> componente, que oferece um modelo controlado por evento. 

Nos dois exemplos, o dormem de thread em segundo plano por um segundo simular trabalho sendo feito nesse thread. 

Você pode compilar e executar esses exemplos que os aplicativos do .NET Framework a C# ou a linha de comando do Visual Basic. Para obter mais informações, consulte [linha de comando compilando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [compilar da linha de comando (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Começando com o .NET Core 3.0, você pode também compilar e executar os exemplos de como os aplicativos .NET Core do Windows de uma pasta que tem um .NET Core Windows Forms  *\<nome da pasta >. csproj* arquivo de projeto. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Exemplo: Use o método Invoke com um delegado

O exemplo a seguir demonstra um padrão para garantir que as chamadas de thread-safe para um controle dos Windows Forms. Ele consulta o <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> propriedade, que compara o controle da criação de ID do thread para a chamada ID do thread. Se as IDs de thread são os mesmos, ele chama o controle diretamente. Se as IDs de thread são diferentes, ele chama o <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> método com um delegado do thread principal, que faz a chamada real para o controle.

O `SafeCallDelegate` permite que a configuração de <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.TextBox.Text%2A> propriedade. O `WriteTextSafe` consultas de método <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Se <xref:System.Windows.Forms.Control.InvokeRequired%2A> retorna `true`, `WriteTextSafe` passa a `SafeCallDelegate` para o <xref:System.Windows.Forms.Control.Invoke%2A> método para fazer a chamada real para o controle. Se <xref:System.Windows.Forms.Control.InvokeRequired%2A> retorna `false`, `WriteTextSafe` define o <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> diretamente. O `Button1_Click` manipulador de eventos cria o novo thread e executa o `WriteTextSafe` método. 

 [!code-csharp[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Exemplo: Usar um manipulador de evento BackgroundWorker

Uma maneira fácil de implementar multithreading é com o <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> componente, que usa um modelo controlado por evento. O thread em segundo plano é executado o <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> evento, que não interage com o thread principal. O thread principal executa o <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> e <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> manipuladores de eventos, que podem chamar controles do thread principal.

Para fazer uma chamada thread-safe usando <xref:System.ComponentModel.BackgroundWorker>, crie um método no thread de segundo plano para fazer o trabalho e associá-lo para o <xref:System.ComponentModel.BackgroundWorker.DoWork> eventos. Crie outro método no thread principal para relatar os resultados do trabalho em segundo plano e associá-lo para o <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> ou <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> eventos. Para iniciar o thread em segundo plano, chame <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>. 

O exemplo usa o <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos para definir o <xref:System.Windows.Forms.TextBox> do controle <xref:System.Windows.Forms.TextBox.Text%2A> propriedade. Para obter um exemplo usando o <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> eventos, consulte <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.BackgroundWorker>
- [Como: Executar uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Como: Implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Desenvolver controles Windows Forms personalizados com o .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
