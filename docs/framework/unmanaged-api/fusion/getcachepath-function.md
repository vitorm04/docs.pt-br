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
ms.openlocfilehash: 13e1468ef5a48f18910c1f8082cdd7c4849da14a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132690"
---
# <a name="getcachepath-function"></a>Função GetCachePath
Obtém o caminho para o assembly armazenado em cache, usando os sinalizadores especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwCacheFlags`  
 no Um valor [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) que indica a origem do assembly armazenado em cache.  
  
 `pwzCachePath`  
 fora O ponteiro retornado para o caminho.  
  
 `pcchPath`  
 [entrada, saída] O comprimento máximo solicitado de `pwzCachePath`e, após o retorno, o comprimento real de `pwzCachePath`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumeração ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)
- [Funções estáticas globais de fusão](fusion-global-static-functions.md)
