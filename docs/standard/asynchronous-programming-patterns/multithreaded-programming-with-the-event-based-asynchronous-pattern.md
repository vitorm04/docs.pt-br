---
title: Programação multithreaded com o padrão assíncrono baseado em evento
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
ms.openlocfilehash: 26e555a158ced352c297952b56f7557cbd825cd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567296"
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a>Programação multithreaded com o padrão assíncrono baseado em evento
Há várias maneiras de expor recursos assíncronos para o código cliente. O Padrão Assíncrono Baseado em Evento prescreve a maneira recomendada de as classes apresentarem comportamento assíncrono.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 Descreve como o Padrão Assíncrono Baseado em Evento disponibiliza as vantagens de aplicativos de vários threads enquanto oculta muitos problemas complexos inerentes ao design com vários threads.  
  
 [Implementando o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 Descreve a maneira padronizada de empacotar uma classe com recursos assíncronos.  
  
 [Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Descreve as exigências para expor recursos assíncronos de acordo com o Padrão Assíncrono Baseado em Evento.  
  
 [Decidindo quando implementar o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Descreve como determinar quando você deve escolher implementar o Padrão Assíncrono Baseado em Evento, em vez do padrão <xref:System.IAsyncResult>.  
  
 [Instruções passo a passo: implementando um componente compatível com o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 Ilustra como criar um componente que implemente o Padrão Assíncrono Baseado em Evento. É implementado usando classes do auxiliar do namespace <xref:System.ComponentModel?displayProperty=nameWithType>, o que garante que o componente funcione corretamente em qualquer modelo de aplicativo.  
  
 [Como usar componentes compatíveis com o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Descreve como usar um componente com suporte ao Padrão Assíncrono Baseado em Evento.  
  
## <a name="reference"></a>Referência  
 <xref:System.ComponentModel.AsyncOperation>  
 Descreve a classe <xref:System.ComponentModel.AsyncOperation> e tem links a todos os seus membros.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Descreve a classe <xref:System.ComponentModel.AsyncOperationManager> e tem links a todos os seus membros.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Descreve o componente <xref:System.ComponentModel.BackgroundWorker> e tem links a todos os seus membros.  
  
## <a name="see-also"></a>Consulte também  
 [Práticas recomendadas de threading gerenciado](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Eventos](../../../docs/standard/events/index.md)  
 [Multithreading em componentes](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
