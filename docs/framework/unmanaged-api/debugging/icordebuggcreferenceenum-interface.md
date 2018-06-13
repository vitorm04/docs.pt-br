---
title: Interface ICorDebugGCReferenceEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa8c3160dc779b2475dec63be896af5283cf5346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418159"
---
# <a name="icordebuggcreferenceenum-interface"></a>Interface ICorDebugGCReferenceEnum
Fornece um enumerador para objetos que serão coletados do lixo.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|Obtém o número especificado de [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instâncias que contêm informações sobre os objetos que serão coletados como lixo.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugGCReferenceEnum` interface implementa a interface de "ICorDebugEnum".  
  
 Um `ICorDebugGCReferenceEnum` instância é populada com [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instâncias chamando o [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) método. [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objetos podem ser enumerados chamando o [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) método.  
  
 O [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objetos na coleção preenchida por este método representam três tipos de objetos:  
  
-   Objetos de todas as pilhas gerenciadas. Isso inclui referências ao vivo em código gerenciado, bem como os objetos criados pelo common language runtime.  
  
-   Objetos da tabela de identificador. Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e variáveis estáticas em um módulo.  
  
-   Objetos de fila do finalizador. Fila do finalizador raízes objetos até que tenha executado o finalizador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
