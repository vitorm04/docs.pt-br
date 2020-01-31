---
title: Método ICLRDataEnumMemoryRegions::EnumMemoryRegions
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: f2b2bbe8bcecf71f6d3016fb35dfbf5ba1353aea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785634"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>Método ICLRDataEnumMemoryRegions::EnumMemoryRegions
Enumera áreas especificadas de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `callback`  
 no Um ponteiro para uma instância de [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) que é chamada por esse método para cada região de memória que está sendo enumerada para notificar o depurador do resultado.  
  
 A enumeração de regiões de memória continua mesmo que o retorno de chamada indique uma falha.  
  
 `miniDumpFlags`  
 no Não usado.  
  
 `clrFlags`  
 no Um valor da enumeração [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) que especifica as regiões de memória a serem enumeradas.  
  
## <a name="remarks"></a>Comentários  
 Esse método usa a instância [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) especificada para notificar o chamador de resultados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataEnumMemoryRegions](iclrdataenummemoryregions-interface.md)
