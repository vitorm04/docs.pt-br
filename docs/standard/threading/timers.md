---
title: Temporizadores
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fca27cf5261e253c2bb3d3a10fa3db31f28a2415
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="timers"></a>Temporizadores
Temporizadores são objetos simples que permitem que você especifique um delegado a ser chamado em um horário especificado. Um thread no pool de threads executa a operação de espera.  
  
 Usando o <xref:System.Threading.Timer?displayProperty=nameWithType> classe é simples. Você cria um **Timer**, passando um <xref:System.Threading.TimerCallback> delegado para o método de retorno de chamada, um objeto que representa o estado que será passado para o retorno de chamada e uma hora inicial acionar uma hora que representa o período entre as chamadas de retorno de chamada. Para cancelar um timer pendentes, chame o **Timer.Dispose** função.  
  
> [!NOTE]
>  Há duas outras classes de temporizador. O <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> classe é um controle que funciona com designers visuais e se destina a ser usado em contextos de interface do usuário; ela gera eventos no thread de interface do usuário. O <xref:System.Timers.Timer?displayProperty=nameWithType> classe derivada de <xref:System.ComponentModel.Component>, portanto ele pode ser usado com designers visuais; ela também gera eventos, mas aumenta em um <xref:System.Threading.ThreadPool> thread. O <xref:System.Threading.Timer?displayProperty=nameWithType> classe torna retornos de chamada em um <xref:System.Threading.ThreadPool> de thread e não usa o modelo de evento. Ele também fornece um objeto de estado para o método de retorno de chamada, que não os outros timers. É extremamente leve.  
  
 O exemplo de código a seguir inicia um temporizador que é iniciado depois de um segundo (1000 milissegundos) e escalas cada segundo até que você pressiona o **Enter** chave. A variável que contém a referência para o timer é um campo de nível de classe, para garantir que o timer não está sujeita à coleta de lixo enquanto ele ainda está em execução. Para obter mais informações sobre a coleta de lixo agressiva, consulte <xref:System.GC.KeepAlive%2A>.  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Timer>  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
