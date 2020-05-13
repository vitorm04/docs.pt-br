---
title: Método ICorDebugRegisterSet::GetRegistersAvailable
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: 74eef0c1ec456d647e5a58e5009d2c77e5002289
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378299"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>Método ICorDebugRegisterSet::GetRegistersAvailable
Obtém uma máscara de bits que indica quais registros neste [ICorDebugRegisterSet](icordebugregisterset-interface.md) estão disponíveis no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAvailable`  
 fora Uma máscara de bits que indica quais registros estão disponíveis no momento.  
  
## <a name="remarks"></a>Comentários  
 Um registro pode não estar disponível se seu valor não puder ser determinado para a situação especificada.  
  
 A máscara retornada contém um bit para cada registro (1 << o índice de registro). O valor de bit será 1 se o registro estiver disponível ou 0 se não estiver disponível.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
- [Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
