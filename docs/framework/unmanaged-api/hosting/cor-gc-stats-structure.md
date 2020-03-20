---
title: Estrutura COR_GC_STATS
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176520"
---
# <a name="cor_gc_stats-structure"></a>Estrutura COR_GC_STATS
Fornece estatísticas sobre o mecanismo de coleta de lixo do tempo de execução da linguagem comum (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`Flags`|Indica quais valores de campo devem ser calculados e devolvidos.|  
|`ExplicitGCCount`|Indica o número de coletas de lixo que foram forçadas por solicitação externa.|  
|`GenCollectionsTaken`|Indica o número de coletas de lixo realizadas para cada geração.|  
|`CommittedKBytes`|O número total de kilobytes cometidos em todos os montes.|  
|`ReservedKBytes`|O número total de kilobytes reservados em todos os montes.|  
|`Gen0HeapSizeKBytes`|O tamanho, em kilobytes, da geração zero.|  
|`Gen1HeapSizeKBytes`|O tamanho, em kilobytes, da geração um pilha.|  
|`Gen2HeapSizeKBytes`|O tamanho, em kilobytes, da geração dois.|  
|`LargeObjectHeapSizeKBytes`|O tamanho, em kilobytes, do grande monte de objetos.|  
|`KBytesPromotedFromGen0`|O tamanho, em kilobytes, dos objetos promovidos da geração zero à geração um.|  
|`KBytesPromotedFromGen1`|O tamanho, em kilobytes, dos objetos promovidos da geração um à geração dois.|  
  
## <a name="remarks"></a>Comentários  
 O método [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) exige `COR_GC_STATS` que o `Flags` campo da estrutura seja definido como um ou mais valores da enumeração [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) para especificar quais estatísticas devem ser definidas.  
  
 A tabela a seguir mapeia as estatísticas fornecidas `COR_GC_COUNTS` por `COR_GC_MEMORYUSAGE`essa estrutura aos dois [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valores de enumeração, e .  
  
|Especificado por COR_GC_COUNTS|Especificado por COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Um exemplo do uso é o seguinte:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Gerenciamento automático de memória](../../../standard/automatic-memory-management.md)
- [Coleta de lixo](../../../standard/garbage-collection/index.md)
