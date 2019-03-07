---
title: Método ICorDebugProcess5::EnumerateGCReferences
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54e2648765d896c189cc2deb5590a0a2a9b3f410
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476472"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>Método ICorDebugProcess5::EnumerateGCReferences
Obtém um enumerador para todos os objetos que precisam estar em um processo de coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `enumerateWeakReferences`  
 [in] Um valor booliano que indica se as referências fracas são também a serem enumerados. Se `enumerateWeakReferences` está `true`, o `ppEnum` enumerador inclui referências fortes e referências fracas. Se `enumerateWeakReferences` é `false`, o enumerador inclui apenas as referências fortes.  
  
 `ppEnum`  
 [out] Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a ser coletado como lixo.  
  
## <a name="remarks"></a>Comentários  
 Esse método fornece uma maneira de determinar a cadeia completa de raiz para qualquer objeto gerenciado em um processo e pode ser usado para determinar por que um objeto ainda está ativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
