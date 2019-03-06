---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: e7bc6f2c96413f3898a17b541733eeecd6a260f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375058"
---
# <a name="ienumrawinputdevice"></a>IEnumRAWINPUTDEVICE
Essa interface enumera os dispositivos de entrada brutos e é usado somente por PresentationHost.exe.  
  
> [!NOTE]
>  Esta API é destinada e tem suporte somente para uso no computador cliente local  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md)|Enumera os próximos `celt` elementos (ou seja, estruturas RAWINPUTDEVICE) na lista do enumerador, retornando-os no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](ienumrawinputdevic-skip.md)|Instrui o enumerador para ignorar a próxima `celt` elementos na enumeração para que a próxima chamada para [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) não retornará esses elementos.|  
|[IEnumRAWINPUTDEVIC:Reset](ienumrawinputdevic-reset.md)|Redefine a sequência de enumeração para o início.|  
|[IEnumRAWINPUTDEVIC:Clone](ienumrawinputdevic-clone.md)|Cria outro enumerador de dispositivo brutos de entrada com o mesmo estado que o enumerador atual para iterar sobre a mesma lista.|  
  
## <a name="see-also"></a>Consulte também
- [Sobre entrada bruta](/windows/desktop/inputdev/about-raw-input)
