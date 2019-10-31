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
ms.openlocfilehash: a3ae474a73f4c8e4b98c4b2bc5d04e55bcae6874
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128662"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a>Método IHostMemoryManager::NeedsVirtualAddressSpace
Notifica o host de que o Common Language Runtime (CLR) tentará usar a memória especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `startAddress`  
 no O endereço inicial da memória.  
  
 `size`  
 no O tamanho, em bytes, da memória.  
  
## <a name="remarks"></a>Comentários  
 O método `NeedsVirtualAddressSpace` é um método de retorno de chamada e deve ser implementado pelo gravador do aplicativo de hospedagem. Ele é chamado pelo CLR.  
  
 Se o host não quiser que o CLR use a memória especificada, ele poderá retornar um E_OUTOFMEMORY HRESULT.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
