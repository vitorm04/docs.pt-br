---
title: Temporizadores
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 478484651bf839f842148f0b4164c9387db3b98a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584951"
---
# <a name="timers"></a>Temporizadores
Os temporizadores são objetos leves que permitem especificar um representante que será chamado em um horário especificado. Um thread no pool de threads executa a operação de espera.  
  
 Com a classe <xref:System.Threading.Timer?displayProperty=nameWithType>, o processo é simples. Você cria um **Temporizador** passando um representante <xref:System.Threading.TimerCallback> para o método de retorno de chamada, um objeto que representa o estado que será passado para o retorno de chamada, um tempo de aumento inicial e um tempo que representa o período entre invocações do retorno de chamada. Para cancelar um temporizador pendente, chame a função **Timer.Dispose**.  
  
> [!NOTE]
>  Há duas outras classes de temporizador. A classe <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> é um controle que funciona com designers visuais e deve ser usada em contextos de interface do usuário. Ela gera eventos no thread da interface do usuário. A classe <xref:System.Timers.Timer?displayProperty=nameWithType> é derivada de <xref:System.ComponentModel.Component>, portanto, pode ser usada com designers visuais. Ela também gera eventos, mas gera-os em um thread <xref:System.Threading.ThreadPool>. A classe <xref:System.Threading.Timer?displayProperty=nameWithType> faz retornos de chamada em um thread <xref:System.Threading.ThreadPool> e não usa o modelo de evento. Ela também fornece um objeto de estado ao método de retorno de chamada que outros temporizadores não fornecem. A classe é extremamente leve.  
  
 O exemplo de código a seguir inicia um temporizador que é iniciado após um segundo (1.000 milissegundos) e marca cada segundo até você pressionar a tecla **Enter**. A variável que contém a referência do temporizador é um campo de nível de classe para garantir que o temporizador não esteja sujeito à coleta de lixo enquanto ele ainda estiver em execução. Para saber mais sobre a coleta de lixo agressiva, confira <xref:System.GC.KeepAlive%2A>.  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Timer>  
 [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)
