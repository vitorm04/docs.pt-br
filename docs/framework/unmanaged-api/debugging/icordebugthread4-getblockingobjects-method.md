---
title: Método ICorDebugThread4::GetBlockingObjects
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55251a3adfa67c1dac3b6952a37217e3eeb4c04a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421899"
---
# <a name="icordebugthread4getblockingobjects-method"></a>Método ICorDebugThread4::GetBlockingObjects
Fornece uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas que fornecem informações de bloqueio de thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppBlockingObjectEnum`  
 [out] Um ponteiro para uma enumeração ordenada de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.  
  
## <a name="remarks"></a>Comentários  
 O primeiro elemento na enumeração retornado corresponde à estrutura primeiro que está bloqueando o thread. O segundo elemento corresponde a um item de bloqueio que é encontrado durante a execução de uma procedimento assíncrona chamada quando bloqueado no primeiro e assim por diante.  
  
 A enumeração é válida apenas para a duração do atual estado sincronizado.  
  
 Esse método deve ser chamado enquanto o depurador está em um estado sincronizado.  
  
 Se `ppBlockingObjectEnum` não é um ponteiro válido, o resultado é indefinido.  
  
 Se um thread está bloqueado e o erro não pode ser determinado, o método retorna um HRESULT que indica falha; Caso contrário, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugThread4](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
