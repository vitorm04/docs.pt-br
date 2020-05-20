---
title: Interface ICLROnEventManager
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 30312e6e09535cee2968b1f9e8ac87b461c5ff40
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703524"
---
# <a name="iclroneventmanager-interface"></a>Interface ICLROnEventManager
Fornece métodos que permitem ao host registrar e cancelar o registro de retornos de chamada para eventos de Common Language Runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md)|Registra um ponteiro de retorno de chamada para o evento especificado.|  
|[Método UnregisterActionOnEvent](iclroneventmanager-unregisteractiononevent-method.md)|Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.|  
  
## <a name="remarks"></a>Comentários  
 Para registrar e cancelar o registro de retornos de chamada de evento, o host obtém uma referência ao `ICLROnEventManager` chamando o método [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) .  
  
> [!NOTE]
> Os eventos descritos por [EClrEvent](eclrevent-enumeration.md) podem ser acionados mais de uma vez e de threads diferentes para sinalizar um descarregamento ou desabilitar o CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Enumeração EClrEvent](eclrevent-enumeration.md)
- [Interface IActionOnCLREvent](iactiononclrevent-interface.md)
- [Interface ICLRControl](iclrcontrol-interface.md)
- [Interfaces de hospedagem](hosting-interfaces.md)
