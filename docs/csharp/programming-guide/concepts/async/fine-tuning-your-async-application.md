---
title: "Ajuste fino de seu aplicativo assíncrono (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d8e655845f2d71e35ac72ba4f5a5b12027e2e1b
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="fine-tuning-your-async-application-c"></a>Ajuste fino de seu aplicativo assíncrono (C#)
É possível adicionar flexibilidade e precisão a seus aplicativos assíncronos usando os métodos e propriedades que o tipo <xref:System.Threading.Tasks.Task> disponibiliza. Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken> e métodos de `Task` importantes como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.  
  
 Usando `WhenAny` e `WhenAll`, é possível, com facilidade, iniciar várias tarefas e aguardar sua conclusão monitorando uma única tarefa.  
  
-   `WhenAny` retorna uma tarefa que é concluída quando qualquer tarefa em uma coleção for concluída.  
  
     Para obter exemplos que usam `WhenAny`, consulte [Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) e [Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).  
  
-   `WhenAll` retorna uma tarefa que é concluída quando todas as tarefas em uma coleção forem concluídas.  
  
     Para obter mais informações e um exemplo que usa `WhenAll`, consulte [Como estender as instruções passo a passo assíncronas usando Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Esta seção inclui os seguintes exemplos.  
  
-   [Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).  
  
-   [Cancelar tarefas assíncronas após um período (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.  
  
 Os projetos criam uma interface do usuário que contém um botão que inicia o processo e um botão que o cancela, como mostra a imagem a seguir. Os botões são chamados `startButton` e `cancelButton`.  
  
 ![Janela do WPF com o botão Cancelar](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancelamento")  
  
 É possível baixar projetos completos do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona com async e await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
