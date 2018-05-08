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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 009f1482de6e1daea21766300b4fb6a3ab0ffc8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corgcstats-structure"></a>Estrutura COR_GC_STATS
Fornece estatísticas sobre o mecanismo de coleta de lixo do common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`Flags`|Indica quais valores de campo devem ser calculados e retornados.|  
|`ExplicitGCCount`|Indica o número de coletas de lixo que foi forçado por solicitação externa.|  
|`GenCollectionsTaken`|Indica o número de coletas de lixo executada para cada geração.|  
|`CommittedKBytes`|O número total de quilobytes confirmada em todos os heaps.|  
|`ReservedKBytes`|O número total de quilobytes reservados em todos os heaps.|  
|`Gen0HeapSizeKBytes`|O tamanho, em quilobytes, do heap de geração de zero.|  
|`Gen1HeapSizeKBytes`|O tamanho, em quilobytes, de geração de um heap.|  
|`Gen2HeapSizeKBytes`|O tamanho, em quilobytes, do heap de geração 2.|  
|`LargeObjectHeapSizeKBytes`|O tamanho, em quilobytes, do heap de objeto grande.|  
|`KBytesPromotedFromGen0`|O tamanho, em quilobytes, dos objetos promovidos da geração de zero para geração de um.|  
|`KBytesPromotedFromGen1`|O tamanho, em quilobytes, dos objetos promovidos da geração de um para geração de dois.|  
  
## <a name="remarks"></a>Comentários  
 O [Iclrgcmanager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) método requer o `Flags` campo o `COR_GC_STATS` estrutura a ser definido para um ou mais valores da [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeração para especificar quais as estatísticas devem ser definidas.  
  
 A tabela a seguir mapeia as estatísticas fornecidas por esta estrutura para os dois [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) valores de enumeração, `COR_GC_COUNTS` e `COR_GC_MEMORYUSAGE`.  
  
|Especificado pelo COR_GC_COUNTS|Especificado pelo COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Um exemplo de uso é o seguinte:  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Gerenciamento Automático de Memória](../../../../docs/standard/automatic-memory-management.md)  
 [Coleta de lixo](../../../../docs/standard/garbage-collection/index.md)
