---
title: Método ICorDebugInternalFrame2::GetFrameAddress
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 51c8f9a2b66d7b2553949056f7cdbedcf5ea37d6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209910"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>Método ICorDebugInternalFrame2::GetFrameAddress
Retorna o endereço da pilha do quadro interno.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAddress`  
 fora Ponteiro para o `CORDB_ADDRESS` para o quadro interno.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O endereço do quadro interno foi retornado com êxito.|  
|E_FAIL|Não foi possível retornar o endereço do quadro interno.|  
|E_INVALIDARG|`pAddress` é `null`.|  
  
## <a name="remarks"></a>Comentários  
 O valor retornado em `pAddress` pode ser usado para determinar o local do quadro interno em relação a outros quadros na pilha. Mesmo em computadores baseados em IA-64, o quadro interno reside somente na pilha e não há nenhum ponteiro correspondente para um repositório de backup.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
