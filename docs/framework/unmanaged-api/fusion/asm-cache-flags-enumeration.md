---
title: Enumeração ASM_CACHE_FLAGS
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 85ac976daec8fd76ee21012a30611235609f4b34
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109488"
---
# <a name="asm_cache_flags-enumeration"></a>Enumeração ASM_CACHE_FLAGS
Indica a origem de um assembly que é representado por [IAssemblyCacheItem](iassemblycacheitem-interface.md) no cache de assembly global.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Enumera o cache de assemblies pré-compilados usando NGen. exe.|  
|`ASM_CACHE_GAC`|Enumera o cache de assembly global.|  
|`ASM_CACHE_DOWNLOAD`|Enumera os assemblies que foram baixados sob demanda ou que foram copiados por sombra.|  
|`ASM_CACHE_ROOT`|Indica que a função [GetCachePath](getcachepath-function.md) deve retornar o caminho para o cache de assembly global para a versão 2,0 do Common Language Runtime (CLR). Significativo apenas no contexto de uma chamada para [GetCachePath](getcachepath-function.md).|  
|`ASM_CACHE_ROOT_EX`|Indica que a função [GetCachePath](getcachepath-function.md) deve retornar o caminho para o cache de assembly global para CLR versão 4. Significativo apenas no contexto de uma chamada para [GetCachePath](getcachepath-function.md).|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função GetCachePath](getcachepath-function.md)
- [Interface IAssemblyCacheItem](iassemblycacheitem-interface.md)
- [Enumerações de fusão](fusion-enumerations.md)
