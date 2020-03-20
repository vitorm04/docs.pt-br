---
title: Faça chamadas seguras para controles
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
ms.openlocfilehash: 365b1acb693b9ff2be603a3e659ed8d846a7696a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141998"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Como: Fazer chamadas seguras para threads para controles do Windows Forms

O multithreading pode melhorar o desempenho dos aplicativos do Windows Forms, mas o acesso aos controles do Windows Forms não é inerentemente seguro para threads. Multithreading pode expor seu código a bugs muito sérios e complexos. Dois ou mais fios manipulando um controle podem forçar o controle a um estado inconsistente e levar a condições de raça, impasses e congelamentos ou travamentos. Se você implementar multithreading em seu aplicativo, certifique-se de chamar controles de linha cruzada de forma segura a thread. Para obter mais informações, consulte [As práticas recomendadas de rosca gerenciadas](../../../standard/threading/managed-threading-best-practices.md).

Existem duas maneiras de chamar com segurança um controle de Formulários do Windows a partir de um segmento que não criou esse controle. Você pode <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> usar o método para chamar um delegado criado no segmento principal, que por sua vez chama o controle. Ou, você pode <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>implementar um , que usa um modelo orientado a eventos para separar o trabalho feito no segmento de fundo de reportar sobre os resultados.

## <a name="unsafe-cross-thread-calls"></a>Chamadas transversais inseguras

Não é seguro chamar um controle diretamente de um segmento que não o criou. O seguinte trecho de código ilustra uma <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> chamada insegura para o controle. O `Button1_Click` manipulador de `WriteTextUnsafe` eventos cria um novo segmento, que define diretamente a propriedade do <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> segmento principal.

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

O depurador do Visual Studio detecta <xref:System.InvalidOperationException> essas chamadas de thread inseguras levantando uma com a mensagem, **a operação cross-thread não é válida. Controle "" acessado a partir de um segmento diferente do segmento em que foi criado.** O <xref:System.InvalidOperationException> sempre ocorre para chamadas transversais inseguras durante a depuração do Visual Studio, e pode ocorrer em tempo de execução do aplicativo. Você deve corrigir o problema, mas você pode <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> desativar `false`a exceção definindo a propriedade para .

## <a name="safe-cross-thread-calls"></a>Chamadas seguras de linha cruzada

Os exemplos de código a seguir demonstram duas maneiras de chamar com segurança um controle do Windows Forms a partir de um segmento que não o criou:

1. O <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> método, que chama um delegado do segmento principal para chamar o controle.
2. Um <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> componente, que oferece um modelo orientado por eventos.

Em ambos os exemplos, o fio de fundo dorme por um segundo para simular o trabalho que está sendo feito nesse segmento.

Você pode criar e executar esses exemplos como aplicativos .NET Framework a partir da linha de comando C# ou Visual Basic. Para obter mais informações, consulte [a construção da linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou Build a partir da linha de comando [(Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Começando com o .NET Core 3.0, você também pode criar e executar os exemplos como aplicativos Windows .NET Core a partir de uma pasta que tem um nome de pasta .NET Core Windows Forms * \<>.csproj* project file.

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Exemplo: Use o método Invocar com um delegado

O exemplo a seguir demonstra um padrão para garantir chamadas seguras de rosca para um controle do Windows Forms. Ele consulta <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> a propriedade, que compara a criação do ID de thread do controle com o ID de segmento de chamada. Se os IDs de rosca forem os mesmos, ele chamará o controle diretamente. Se os IDs de segmento <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> forem diferentes, ele chama o método com um delegado do segmento principal, o que torna a chamada real para o controle.

O `SafeCallDelegate` habilita <xref:System.Windows.Forms.TextBox> restatando a propriedade do <xref:System.Windows.Forms.TextBox.Text%2A> controle. As `WriteTextSafe` consultas <xref:System.Windows.Forms.Control.InvokeRequired%2A>do método . Se <xref:System.Windows.Forms.Control.InvokeRequired%2A> `true`retornar, `WriteTextSafe` `SafeCallDelegate` passa <xref:System.Windows.Forms.Control.Invoke%2A> o método para fazer a chamada real para o controle. Se <xref:System.Windows.Forms.Control.InvokeRequired%2A> `false`retornar, `WriteTextSafe` <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> defina o diretamente. O `Button1_Click` manipulador de eventos cria `WriteTextSafe` o novo segmento e executa o método.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Exemplo: Use um manipulador de eventos BackgroundWorker

Uma maneira fácil de implementar multithreading é com o <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> componente, que usa um modelo orientado por eventos. O segmento de <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> fundo executa o evento, que não interage com o segmento principal. O segmento principal <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> executa os manipuladores e os manipuladores de eventos, que podem chamar os controles do segmento principal.

Para fazer uma chamada segura <xref:System.ComponentModel.BackgroundWorker>de rosca usando, crie um método no segmento <xref:System.ComponentModel.BackgroundWorker.DoWork> de fundo para fazer o trabalho e vincule-o ao evento. Crie outro método no segmento principal para relatar os resultados do <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> trabalho de fundo e vinculá-lo ao evento. Para iniciar o segmento <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>de fundo, ligue .

O exemplo <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> usa o manipulador <xref:System.Windows.Forms.TextBox> de <xref:System.Windows.Forms.TextBox.Text%2A> eventos para definir a propriedade do controle. Para um exemplo <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> usando <xref:System.ComponentModel.BackgroundWorker>o evento, consulte .

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Confira também

- <xref:System.ComponentModel.BackgroundWorker>
- [Como: Executar uma operação em segundo plano](how-to-run-an-operation-in-the-background.md)
- [Como: Implementar um formulário que usa uma operação de fundo](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Desenvolva controles personalizados do Windows Forms com o .NET Framework](developing-custom-windows-forms-controls.md)
