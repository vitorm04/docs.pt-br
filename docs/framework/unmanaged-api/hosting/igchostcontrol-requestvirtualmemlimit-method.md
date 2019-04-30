---
title: Método IGCHostControl::RequestVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948b18832ccfc5e0fc2e42ee58e6444a581de260
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968266"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a>Método IGCHostControl::RequestVirtualMemLimit
Solicitações de host para alterar os limites de memória virtual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `sztMaxVirtualMemMB`  
 [in] O tamanho solicitado da alocação de memória.  
  
 `psztNewMaxVirtualMemMB`  
 [no, out] Um ponteiro para o tamanho real da memória alocada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
