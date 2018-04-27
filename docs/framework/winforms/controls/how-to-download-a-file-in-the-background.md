---
title: Como baixar um arquivo no segundo plano
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bdc587fb42722108466361500816a6598c8515e9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-download-a-file-in-the-background"></a>Como baixar um arquivo no segundo plano
Baixar um arquivo é uma tarefa comum e costuma ser útil executar esta operação potencialmente demorada em um thread separado. Use o <xref:System.ComponentModel.BackgroundWorker> componente para realizar essa tarefa com muito pouco código.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar um <xref:System.ComponentModel.BackgroundWorker> componente para carregar um arquivo XML de uma URL. Quando o usuário clica o **baixar** botão, o <xref:System.Windows.Forms.Control.Click> chamadas de manipulador de eventos de <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método de um <xref:System.ComponentModel.BackgroundWorker> componente para iniciar a operação de download. O botão é desabilitado durante o download e então habilitado quando o download for concluído. Um <xref:System.Windows.Forms.MessageBox> exibe o conteúdo do arquivo.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Baixando o arquivo**  
  
 O arquivo é baixado no <xref:System.ComponentModel.BackgroundWorker> thread de trabalho do componente, que executa o <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos. Esse thread é iniciado quando seu código chama o <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> método.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **Aguardando a conclusão de um BackgroundWorker**  
  
 O `downloadButton_Click` manipulador de eventos demonstra como aguardar um <xref:System.ComponentModel.BackgroundWorker> componente para concluir sua tarefa assíncrona.  
  
 Se você só deseja que o aplicativo responda a eventos e não quer realizar trabalhos no thread principal enquanto aguarda o thread em segundo plano concluir, basta sair do manipulador.  
  
 Se você quiser continuar a fazer o trabalho do thread principal, use o <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> propriedade para determinar se o <xref:System.ComponentModel.BackgroundWorker> thread ainda está em execução. No exemplo, uma barra de progresso é atualizada enquanto o download é processado. Certifique-se de chamar o <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> método para manter a interface do usuário responsiva.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Exibindo o resultado**  
  
 O `backgroundWorker1_RunWorkerCompleted` método trata o <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> eventos e é chamado quando a operação em segundo plano é concluída. Este método verifica primeiro o <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> propriedade. Se <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> é `null`, em seguida, esse método exibe o conteúdo do arquivo. Ele habilita então o botão de download, que estava desabilitado quando o download começou, e reinicia a barra de progresso.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System.Drawing, System.Windows.Forms e System.Xml.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Programação robusta  
 Sempre verifique o <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> propriedade em seu <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> manipulador de eventos antes de tentar acessar o <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> propriedade ou qualquer outro objeto afetado pelo <xref:System.ComponentModel.BackgroundWorker.DoWork> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Como executar uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Como implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
