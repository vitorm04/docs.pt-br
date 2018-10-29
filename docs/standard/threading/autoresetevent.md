---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 519776b5c1c237deb520476384495b8dd96a4e39
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201300"
---
# <a name="autoresetevent"></a>AutoResetEvent
A classe <xref:System.Threading.AutoResetEvent> representa um evento de identificador de espera local que redefine automaticamente quando sinalizado, após o lançamento de um único thread de espera. Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle>. Consulte a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição automática.  
  
 Um objeto <xref:System.Threading.AutoResetEvent> é redefinido automaticamente para ser não sinalizado pelo sistema depois que um único thread de espera for liberado. Se nenhum thread estiver aguardando, o estado do objeto de evento permanecerá sinalizado.
  
 Para obter um exemplo que usa <xref:System.Threading.AutoResetEvent>, confira <xref:System.Threading.Monitor>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Objetos e recursos de threading](threading-objects-and-features.md)  
- [Threading](index.md)  
