---
title: Chamando métodos assíncronos usando IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121307"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>Chamando métodos assíncronos usando IAsyncResult
Tipos em bibliotecas de classes de terceiros e no .NET Framework podem fornecer métodos que permitem que um aplicativo continue a ser executado durante o desempenho de operações assíncronas em threads diferentes do thread principal do aplicativo. As seções a seguir descrevem e fornecem exemplos de código que demonstram diferentes maneiras de chamar métodos assíncronos que usam o padrão de design <xref:System.IAsyncResult>.  
  
- [Bloqueando a execução do aplicativo terminando uma operação de sincronização](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- [Bloqueando a execução do aplicativo usando um AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [Votação para o Status de uma Operação Assíncrona](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Usando um Delegado AsyncCallback para acabar com uma operação assíncrona](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Confira também

- [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Visão geral do padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
