---
title: Interface IHostPolicyManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager
helpviewer_keywords: IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8f49474f1a75af91ac5296be866914e05732e755
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanager-interface"></a>Interface IHostPolicyManager
Fornece métodos que notificam o host das ações que executa o common language runtime (CLR) no caso do anula, tempos limites ou falhas.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método OnDefaultAction](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Notifica o host que o CLR está prestes a realizar a ação padrão especificada por uma chamada para [SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) em resposta a um thread de anulação ou <xref:System.AppDomain> descarregar.|  
|[Método OnFailure](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|Notifica o host que o CLR está prestes a realizar a ação especificada por uma chamada para [SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) em resposta a uma falha de alocação ou recuperação de recursos.|  
|[Método OnTimeout](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|Notifica o host que o CLR está prestes a realizar a ação especificada por uma chamada para [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) em resposta a um tempo limite.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [Enumeração EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [Enumeração EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [Interfaces de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
