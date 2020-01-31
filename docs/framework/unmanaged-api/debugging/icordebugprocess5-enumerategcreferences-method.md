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
ms.openlocfilehash: 81993f108ae9b59300b5d29402d7a423c3657757
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792441"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>Método ICorDebugProcess5::EnumerateGCReferences
Obtém um enumerador para todos os objetos que devem ser coletados pelo lixo em um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `enumerateWeakReferences`  
 no Um valor booliano que indica se referências fracas também devem ser enumeradas. Se `enumerateWeakReferences` for `true`, o enumerador `ppEnum` incluirá referências fortes e referências fracas. Se `enumerateWeakReferences` for `false`, o enumerador incluirá apenas referências fortes.  
  
 `ppEnum`  
 fora Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a serem coletados como lixo.  
  
## <a name="remarks"></a>Comentários  
 Esse método fornece uma maneira de determinar a cadeia de raiz completa para qualquer objeto gerenciado em um processo e pode ser usado para determinar por que um objeto ainda está ativo.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugProcess5](icordebugprocess5-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
