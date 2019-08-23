---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964773"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Essa interface enumera os dispositivos de entrada brutos e é usada somente pelo PresentationHost. exe.  
  
> [!NOTE]
> Esta API é destinada e tem suporte somente para uso no computador cliente local  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Enumera os elementos seguintes `celt` (ou seja, estruturas RAWINPUTDEVICE) na lista do enumerador, retornando `rgelt` -os junto com o número real de elementos enumerados no `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Instrui o enumerador a ignorar os próximos `celt` elementos na enumeração para que a próxima chamada para [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) não retorne esses elementos.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Redefine a sequência de enumeração para o início.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Cria outro enumerador de dispositivo de entrada bruto com o mesmo estado que o enumerador atual para iterar na mesma lista.|  
  
## <a name="see-also"></a>Consulte também

- [Sobre a entrada bruta](/windows/desktop/inputdev/about-raw-input)
