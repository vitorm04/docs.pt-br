---
title: Como implementar um formulário que use uma operação em segundo plano
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 5923895e1e6cf86f8de30405dbfdb0a603d708d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533290"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Como implementar um formulário que use uma operação em segundo plano
O programa de exemplo a seguir cria um formulário que calcula números Fibonacci. O cálculo é executado em um thread que está separado do thread da interface do usuário, para que a interface do usuário continuará a ser executado sem atrasos conforme o cálculo prossegue.  
  
 Há um suporte abrangente para esta tarefa no Visual Studio.  
  
 Consulte também [passo a passo: Implementando um formulário que usa uma operação em segundo plano](http://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Programação robusta  
  
> [!CAUTION]
>  O uso de multithreading de qualquer tipo pode expor o computador a bugs muito sérios e complexos. Consulte as [Melhores práticas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md) antes de implementar qualquer solução que use multithreading.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Práticas recomendadas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md)
