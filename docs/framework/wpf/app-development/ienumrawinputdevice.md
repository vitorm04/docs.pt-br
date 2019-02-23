---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: e07b646c51a143cc15fd125dc295ed90f605328f
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745645"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Essa interface enumera os dispositivos de entrada brutos e é usado somente por PresentationHost.exe.  
  
> [!NOTE]
>  Esta API é destinada e tem suporte somente para uso no computador cliente local  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|Enumera os próximos `celt` elementos (ou seja, estruturas RAWINPUTDEVICE) na lista do enumerador, retornando-os no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|Instrui o enumerador para ignorar a próxima `celt` elementos na enumeração para que a próxima chamada para [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) não retornará esses elementos.|  
|[IEnumRAWINPUTDEVIC:Reset](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|Redefine a sequência de enumeração para o início.|  
|[IEnumRAWINPUTDEVIC:Clone](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|Cria outro enumerador de dispositivo brutos de entrada com o mesmo estado que o enumerador atual para iterar sobre a mesma lista.|  
  
## <a name="see-also"></a>Consulte também
- [Sobre entrada bruta](/windows/desktop/inputdev/about-raw-input)
