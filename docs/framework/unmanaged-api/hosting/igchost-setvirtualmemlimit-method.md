---
title: Método IGCHost::SetVirtualMemLimit
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b25e9c738c95a918b79d3fd324787e4aaf3aaa7f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502469"
---
# <a name="igchostsetvirtualmemlimit-method"></a>Método IGCHost::SetVirtualMemLimit
Define o tamanho máximo de memória de virtual do tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `sztMaxVirtualMemMB`  
 [in] O tamanho máximo, em megabytes, da memória virtual do tempo de execução.  
  
## <a name="remarks"></a>Comentários  
 O tamanho máximo de memória de virtual do tempo de execução pode ser alterado dinamicamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl, GCHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
