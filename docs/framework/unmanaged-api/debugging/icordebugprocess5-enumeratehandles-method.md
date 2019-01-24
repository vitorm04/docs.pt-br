---
title: Método ICorDebugProcess5::EnumerateHandles
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b8c3f102405c9b9fa9af2597658b728e618cabb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559366"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>Método ICorDebugProcess5::EnumerateHandles
Obtém um enumerador para os identificadores de objeto em um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `types`  
 [in] Uma combinação bit a bit de [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valores que especifica o tipo de identificadores para incluir na coleção.  
  
 `ppENum`  
 [out] Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a ser coletado como lixo.  
  
## <a name="remarks"></a>Comentários  
 `EnumerateHandles` é uma função auxiliar que dá suporte a inspeção da tabela de identificador. É semelhante ao [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) método, exceto que, em vez de preencher uma [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) coleção com todos os objetos a ser coletado como lixo, ele inclui apenas os objetos que têm identificadores da tabela de identificador.  
  
 O `types` parâmetro especifica os tipos de identificador para incluir na coleção. `types` pode ser qualquer um dos seguintes três membros do [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeração:  
  
-   `CorHandleStrongOnly` (as alças para apenas referências fortes).  
  
-   `CorHandleWeakOnly` (as alças para referências fracas apenas).  
  
-   `CorHandleAll` (todos os identificadores).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
