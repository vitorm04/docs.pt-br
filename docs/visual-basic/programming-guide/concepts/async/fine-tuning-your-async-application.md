---
title: "Ajustando seu aplicativo Async (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ajustando seu aplicativo Async (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode adicionar flexibilidade e precisão aos seus aplicativos assíncronos usando os métodos e propriedades que o <xref:System.Threading.Tasks.Task> tipo disponibiliza. Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken> e importante `Task` métodos como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.  
  
 Usando `WhenAny` e `WhenAll`, você pode iniciar várias tarefas e aguardar sua conclusão por uma única tarefa de monitoramento mais facilmente.  
  
-   `WhenAny` Retorna uma tarefa concluída quando qualquer tarefa em uma coleção for concluída.  
  
     Para obter exemplos que usam `WhenAny`, consulte  [Cancelar as demais tarefas assíncronas após um completo \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)e [Iniciar várias tarefas assíncronas e processá\-las assim que são concluídas \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` Retorna uma tarefa concluída quando todas as tarefas em uma coleção forem concluídas.  
  
     Para obter mais informações e um exemplo que usa `WhenAll`, consulte [Como: estender o passo a passo assíncronas usando Task. WhenAll \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Esta seção inclui os exemplos a seguir.  
  
-   [Cancelar uma tarefa assíncrona ou uma lista de tarefas \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Cancelar tarefas assíncronas após um período de tempo \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Cancelar as demais tarefas assíncronas após um completo \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Iniciar várias tarefas assíncronas e processá\-las assim que são concluídas \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
 Os projetos de criar uma interface do usuário que contém um botão que inicia o processo e um botão cancela, como mostra a imagem a seguir. Os botões são denominados `startButton` e `cancelButton`.  
  
 ![Janela do WPF com o botão Cancelar](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")  
  
 Você pode baixar os projetos Windows Presentation Foundation \(WPF\) completa de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
## Consulte também  
 [Programação assíncrona com Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)