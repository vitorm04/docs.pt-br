---
title: Visão geral do componente BackgroundWorker
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: d7d99cf87507237b23cb40c58b2308643f7f1056
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872186"
---
# <a name="backgroundworker-component-overview"></a>Visão geral do componente BackgroundWorker
Há muitas operações realizadas com frequência que podem levar muito tempo para serem executadas. Por exemplo:  
  
-   Downloads de imagens  
  
-   Invocações de serviço Web  
  
-   Downloads e uploads de arquivos (inclusive de aplicativos ponto a ponto)  
  
-   Cálculos locais complexos  
  
-   Transações de banco de dados  
  
-   Acesso ao disco local, dada a sua baixa velocidade em relação ao acesso à memória  
  
 Operações como essas podem fazer com que a sua interface de usuário pare de responder enquanto elas estiverem em execução. Se você quer uma interface que responda com agilidade e está enfrentando longos atrasos associados a essas operações, o componente <xref:System.ComponentModel.BackgroundWorker> fornece uma solução conveniente.  
  
 O componente <xref:System.ComponentModel.BackgroundWorker> possibilita executar operações demoradas de forma assíncrona ("no segundo plano"), em um thread diferente do thread principal da interface do usuário do aplicativo. Para usar um <xref:System.ComponentModel.BackgroundWorker>, basta indicar o método de trabalho demorado que será executado em segundo plano e chamar o método <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>. Seu thread de chamada continua a funcionar normalmente enquanto o método de trabalho é executado de forma assíncrona. Quando o método é concluído, o <xref:System.ComponentModel.BackgroundWorker> alerta o thread de chamada disparando o evento <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, que contém, opcionalmente, os resultados da operação.  
  
 O <xref:System.ComponentModel.BackgroundWorker> componente está disponível em de **caixa de ferramentas**, no **componentes** guia. Para adicionar um <xref:System.ComponentModel.BackgroundWorker> ao seu formulário, arraste o componente <xref:System.ComponentModel.BackgroundWorker> para o seu formulário. Ele aparece na bandeja de componentes e suas propriedades aparecem na janela **Propriedades**.  
  
 Para iniciar a operação assíncrona, use o método <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>. <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> usa um parâmetro opcional `object`, que pode ser usado para passar argumentos para o seu método de trabalho. A classe <xref:System.ComponentModel.BackgroundWorker> expõe o evento <xref:System.ComponentModel.BackgroundWorker.DoWork>, ao qual o seu thread de trabalho está anexado por meio de um manipulador de eventos <xref:System.ComponentModel.BackgroundWorker.DoWork>.  
  
 O manipulador de eventos <xref:System.ComponentModel.BackgroundWorker.DoWork> usa um parâmetro <xref:System.ComponentModel.DoWorkEventArgs>, que tem uma propriedade <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>. Esta propriedade recebe o parâmetro de <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> e pode ser passada para o seu método de trabalho, que será chamado no manipulador de eventos <xref:System.ComponentModel.BackgroundWorker.DoWork>. O exemplo a seguir mostra como atribuir um resultado de um método de trabalho chamado `ComputeFibonacci`. Ele faz parte de um exemplo maior, que pode ser encontrado em [Como implementar um formulário que usa uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 Para obter mais informações sobre o uso de manipuladores de eventos, consulte [Eventos](../../../../docs/standard/events/index.md).  
  
> [!CAUTION]
>  O uso de multithreading de qualquer tipo pode expor o computador a bugs muito sérios e complexos. Consulte as [Melhores práticas de threading gerenciado](../../../../docs/standard/threading/managed-threading-best-practices.md) antes de implementar qualquer solução que use multithreading.  
  
 Para obter mais informações sobre como usar o <xref:System.ComponentModel.BackgroundWorker> classe, consulte [como: executar uma operação em segundo plano](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
## <a name="see-also"></a>Consulte também

- [Threading gerenciado](../../../../docs/standard/threading/index.md)
- [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Como implementar um formulário que usa uma operação em segundo plano](how-to-implement-a-form-that-uses-a-background-operation.md)
