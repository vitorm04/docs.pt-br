---
title: Threads em primeiro plano e em segundo plano
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ad427fc2c1175c0d9b333aa418aea039f11a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="foreground-and-background-threads"></a>Threads em primeiro plano e em segundo plano
Um thread gerenciado é um thread em segundo plano ou em um thread de primeiro plano. Threads em segundo plano são idênticos aos threads de primeiro plano com uma exceção: um thread em segundo plano não manter o ambiente de execução gerenciado em execução. Depois que todos os threads de primeiro plano tem sido interrompidos em um processo gerenciado (onde o arquivo .exe é um assembly gerenciado), o sistema interrompe todos os threads em segundo plano e desligado.  
  
> [!NOTE]
>  Quando o tempo de execução para um thread em segundo plano porque o processo está sendo desligado, nenhuma exceção é lançada no thread. No entanto, quando threads foram interrompidos, pois o <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> método descarrega o domínio de aplicativo, um <xref:System.Threading.ThreadAbortException> é gerada em threads de primeiro plano e plano de fundo.  
  
 Use o <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> propriedade para determinar se um thread é um plano de fundo ou um thread de primeiro plano ou para alterar seu status. Um thread pode ser alterado para um thread em segundo plano a qualquer momento, definindo seu <xref:System.Threading.Thread.IsBackground%2A> propriedade `true`.  
  
> [!IMPORTANT]
>  O status de primeiro plano ou plano de fundo de um thread não afeta o resultado de uma exceção sem tratamento no thread. No .NET Framework versão 2.0, uma exceção sem tratamento em threads de primeiro plano ou segundo plano resulta no encerramento do aplicativo. Consulte [exceções em Threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Threads que pertencem ao pool de threads gerenciados (ou seja, threads cujo <xref:System.Threading.Thread.IsThreadPoolThread%2A> é de propriedade `true`) threads em segundo plano. Todos os threads que insira o ambiente de execução gerenciado de código não gerenciado são marcados como threads em segundo plano. Todos os threads gerados ao criar e iniciar um novo <xref:System.Threading.Thread> objeto são por threads de primeiro plano padrão.  
  
 Se você usar um thread para monitorar uma atividade, como uma conexão de soquete, defina seu <xref:System.Threading.Thread.IsBackground%2A> propriedade `true` para que o thread não impede que o processo de encerramento.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
