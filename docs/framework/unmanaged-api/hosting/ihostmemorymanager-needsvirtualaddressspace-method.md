---
title: Método IHostMemoryManager::NeedsVirtualAddressSpace
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fe47a155b29fe452a59adfaffe59162f60f58aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469568"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>Método IHostMemoryManager::NeedsVirtualAddressSpace
Notifica o host que o common language runtime (CLR) vai tentar usar a memória especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `startAddress`  
 [in] O endereço inicial da memória.  
  
 `size`  
 [in] O tamanho, em bytes, da memória.  
  
## <a name="remarks"></a>Comentários  
 O `NeedsVirtualAddressSpace` é um método de retorno de chamada de método e deve ser implementado pelo gravador do aplicativo host. Ele é chamado pelo CLR.  
  
 Se o host não quiser que o CLR para usar a memória especificada, ele poderá retornar um HRESULT E_OUTOFMEMORY.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
