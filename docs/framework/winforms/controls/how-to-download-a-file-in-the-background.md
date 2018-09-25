---
title: Como baixar um arquivo no segundo plano
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: 2396516a0e6c9aeb9b2d64a0bf6e3974d64a5cc5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071392"
---
# <a name="how-to-download-a-file-in-the-background"></a>Como baixar um arquivo no segundo plano
Baixar um arquivo é uma tarefa comum e costuma ser útil executar esta operação potencialmente demorada em um thread separado. Use o <xref:System.ComponentModel.BackgroundWorker> componente para realizar essa tarefa com pouquíssimo código.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar um <xref:System.ComponentModel.BackgroundWorker> componente para carregar um arquivo XML de uma URL. Quando o usuário clica o **Baixe** botão, o <xref:System.Windows.Forms.Control.Click> chamadas do manipulador de eventos a <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método de um <xref:System.ComponentModel.BackgroundWorker> componente para iniciar a operação de download. O botão é desabilitado durante o download e então habilitado quando o download for concluído. Um <xref:System.Windows.Forms.MessageBox> exibe o conteúdo do arquivo.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Baixando o arquivo**  
  
 O arquivo é baixado no <xref:System.ComponentModel.BackgroundWorker> thread de trabalho do componente, que executa o <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos. Esse thread é iniciado quando seu código chama o <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **Aguardando a conclusão de um BackgroundWorker**  
  
 O `downloadButton_Click` manipulador de eventos demonstra como aguardar um <xref:System.ComponentModel.BackgroundWorker> componente para concluir sua tarefa assíncrona.  
  
 Se você só deseja que o aplicativo responda a eventos e não quer realizar trabalhos no thread principal enquanto aguarda o thread em segundo plano concluir, basta sair do manipulador.  
  
 Se você quiser continuar a fazer o trabalho no thread principal, use o <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> propriedade para determinar se o <xref:System.ComponentModel.BackgroundWorker> segmento ainda está em execução. No exemplo, uma barra de progresso é atualizada enquanto o download é processado. Certifique-se de chamar o <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> método para manter a interface do usuário responsiva.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Exibindo o resultado**  
  
 O `backgroundWorker1_RunWorkerCompleted` identificadores de método a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> evento e é chamado quando a operação em segundo plano seja concluída. Esse método primeiro verifica o <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> propriedade. Se <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> é `null`, em seguida, esse método exibe o conteúdo do arquivo. Ele habilita então o botão de download, que estava desabilitado quando o download começou, e reinicia a barra de progresso.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System.Drawing, System.Windows.Forms e System.Xml.  
  
 Para obter informações sobre como compilar este exemplo de linha de comando do visual Basic ou Visual c#, consulte [compilando da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Programação robusta  
 Sempre verifique o <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> propriedade em seu <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos antes de tentar acessar o <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> propriedade ou qualquer outro objeto que pode ter sido afetado pelo <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Como executar uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Como implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
