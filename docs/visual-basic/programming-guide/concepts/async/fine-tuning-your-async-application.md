---
title: Ajustando seu aplicativo Async (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d0cac2fe7305031b93a375a08e785285a291320
ms.lasthandoff: 03/13/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a>Ajustando seu aplicativo Async (Visual Basic)
Você pode adicionar flexibilidade e precisão aos seus aplicativos assíncronos usando os métodos e propriedades que o <xref:System.Threading.Tasks.Task>tipo disponibiliza.</xref:System.Threading.Tasks.Task> Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken>e importante `Task` métodos como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> </xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> </xref:System.Threading.CancellationToken>  
  
 Usando `WhenAny` e `WhenAll`, você pode iniciar várias tarefas e aguardar sua conclusão por uma única tarefa de monitoramento mais facilmente.  
  
-   `WhenAny`Retorna uma tarefa concluída quando qualquer tarefa em uma coleção for concluída.  
  
     Para obter exemplos que usam `WhenAny`, consulte [Cancelar tarefas de Async restantes após um é concluído (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)e [iniciar várias tarefas assíncronas e processo-los como eles completo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll`Retorna uma tarefa concluída quando todas as tarefas em uma coleção forem concluídas.  
  
     Para obter mais informações e um exemplo que usa `WhenAll`, consulte [como: estender o Async Walkthrough por usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Esta seção inclui os exemplos a seguir.  
  
-   [Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Cancelar tarefas assíncronas após um período de tempo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Cancelar as demais tarefas assíncronas após um completo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Iniciar várias tarefas assíncronas e processá-las assim que são concluídas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
 Os projetos de criar uma interface do usuário que contém um botão que inicia o processo e um botão cancela, como mostra a imagem a seguir. Os botões são nomeados `startButton` e `cancelButton`.  
  
 ![Janela WPF com o botão Cancelar](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "cancelamento")  
  
 Você pode baixar os projetos Windows Presentation Foundation (WPF) completa de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
