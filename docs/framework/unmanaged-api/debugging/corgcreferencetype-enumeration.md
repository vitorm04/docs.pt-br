---
title: Enumeração CorGCReferenceType
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 822425b958422ba364a1f10903c7c312ba43fab9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corgcreferencetype-enumeration"></a>Enumeração CorGCReferenceType
Identifica a fonte de um objeto para ser coletado do lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a>Membros  
  
|Nome do membro|Descrição|  
|-----------------|-----------------|  
|`CorHandleStrong`|Uma alça para uma referência forte da tabela de identificador de objeto.|  
|`CorHandleStrongPinning`|Um identificador para uma referência forte fixado da tabela de identificador de objeto.|  
|`CorHandleWeakShort`|Um identificador para uma referência fraca da tabela de identificador de objeto.|  
|`CorHandleWeakRefCount`|Um identificador para um objeto de contado por referência fraco da tabela de identificador de objeto.|  
|`CorHandleStrongRefCount`|Um identificador para um objeto contado por referência da tabela de identificador de objeto.|  
|`CorHandleStrongDependent`|Um identificador para um objeto dependente da tabela de identificador de objeto.|  
|`CorHandleStrongAsyncPinned`|Um objeto fixo assíncrono da tabela de identificador de objeto.|  
|`CorHandleStrongSizedByref`|Uma alça forte que mantém um tamanho aproximado do fechamento coletivo de todos os objetos e raízes de objeto no momento da coleta de lixo.|  
|`CorReferenceStack`|Uma referência da pilha gerenciada.|  
|`CorReferenceFinalizer`|Uma referência de fila do finalizador.|  
|CorHandleStrongOnly|Retorne apenas referências fortes da tabela de identificador. Esse valor é usado pelo [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) método apenas.|  
|`CorHandleWeakOnly`|Retorne apenas referências fracas da tabela de identificador. Esse valor é usado pelo [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) método apenas.|  
|`CorHandleAll`|Retorne todas as referências da tabela de identificador. Esse valor é usado pelo [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) método apenas.|  
  
## <a name="remarks"></a>Comentários  
 O `CorGCReferenceType` enumeração é usada da seguinte maneira:  
  
-   Como o valor da `type` campo do [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) estrutura, ele indica que a fonte de uma referência ou um identificador.  
  
-   Como o `types` argumento para o [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) método, especifica os tipos de identificadores para incluir na enumeração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
