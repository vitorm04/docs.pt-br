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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22dfa99d8069c060a525a9ae2cbef73d6625898
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434097"
---
# <a name="iclroneventmanager-interface"></a>Interface ICLROnEventManager
Fornece métodos que permitem que o host registrar e cancelar o registro de retornos de chamada para eventos de tempo de execução (CLR) de linguagem comum.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|Registra um ponteiro de retorno de chamada para o evento especificado.|  
|[Método UnregisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|Cancela o registro de um ponteiro de retorno de chamada registrado anteriormente para o evento especificado.|  
  
## <a name="remarks"></a>Comentários  
 Para registrar e cancelar o registro de retornos de chamada de evento, o host obtém uma referência a `ICLROnEventManager` chamando o [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método.  
  
> [!NOTE]
>  Os eventos descritos por [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) podem ser acionados mais de uma vez e de diversos threads para sinalizar um descarregamento ou a desabilitação do CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [Interface IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
