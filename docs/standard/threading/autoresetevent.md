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
ms.openlocfilehash: 7602a61a4403b7ab85015876823aa41e250b23de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863303"
---
# <a name="autoresetevent"></a>AutoResetEvent
A classe <xref:System.Threading.AutoResetEvent> representa um evento de identificador de espera local que redefine automaticamente quando sinalizado, após o lançamento de um único thread de espera. Essa classe representa um caso especial de sua classe base, <xref:System.Threading.EventWaitHandle>. Consulte a documentação conceitual de [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) para conhecer o uso e os recursos de eventos de redefinição automática.  
  
 Um objeto <xref:System.Threading.AutoResetEvent> é redefinido automaticamente para ser não sinalizado pelo sistema depois que um único thread de espera for liberado. Se nenhum thread estiver aguardando, o estado do objeto de evento permanecerá sinalizado. <xref:System.Threading.AutoResetEvent> corresponde a uma chamada Win32 `CreateEvent`, especificando `false` para o argumento `bManualReset`.  
  
 Para obter um exemplo que usa <xref:System.Threading.AutoResetEvent>, confira <xref:System.Threading.Monitor>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Threading](../../../docs/standard/threading/index.md)  
- [Objetos e recursos de threading](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Identificadores de espera](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
