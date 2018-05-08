---
title: Função GetCachePath
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42bae646b0b1cdd451e01d55ed5b218f3660bb5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getcachepath-function"></a>Função GetCachePath
Obtém o caminho para o assembly em cache, usando os sinalizadores especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCacheFlags`  
 [in] Um [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) valor que indica a origem do assembly em cache.  
  
 `pwzCachePath`  
 [out] O ponteiro retornado para o caminho.  
  
 `pcchPath`  
 [out no] O tamanho máximo solicitado da `pwzCachePath`e no retorno, o comprimento real da `pwzCachePath`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [Funções estáticas globais de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
