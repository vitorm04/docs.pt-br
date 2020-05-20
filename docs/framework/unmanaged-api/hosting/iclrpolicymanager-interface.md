---
title: Interface ICLRPolicyManager
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703483"
---
# <a name="iclrpolicymanager-interface"></a>Interface ICLRPolicyManager
Fornece métodos que permitem que o host especifique ações de política a serem executadas em caso de falhas e tempos limite.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md)|Especifica a ação de política que o Common Language Runtime (CLR) deve executar quando a falha especificada ocorrer.|  
|[Método SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)|Especifica a ação de política que o CLR deve executar quando a operação especificada atingir o tempo limite.|  
|[Método SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md)|Especifica a ação de política que o CLR deve executar quando a operação especificada ocorre.|  
|[Método SetTimeout](iclrpolicymanager-settimeout-method.md)|Define um valor de tempo limite para a operação especificada.|  
|[Método SetTimeoutAndAction](iclrpolicymanager-settimeoutandaction-method.md)|Define um valor de tempo limite para a operação especificada e especifica a ação de política que o CLR deve executar quando a operação ocorre.|  
|[Método SetUnhandledExceptionPolicy](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|Especifica o comportamento do CLR quando ocorre uma exceção sem tratamento.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Enumeração EClrFailure](eclrfailure-enumeration.md)
- [Enumeração EClrOperation](eclroperation-enumeration.md)
- [Enumeração EPolicyAction](epolicyaction-enumeration.md)
- [Interface ICLRControl](iclrcontrol-interface.md)
