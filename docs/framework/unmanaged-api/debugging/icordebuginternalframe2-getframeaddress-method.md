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
ms.openlocfilehash: 967c0e18b354e6e1cd0d87900e3cde85991c0862
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794322"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a>Método ICorDebugInternalFrame2::GetFrameAddress
Retorna o endereço da pilha do quadro interno.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pAddress`  
 fora Ponteiro para a `CORDB_ADDRESS` do quadro interno.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O endereço do quadro interno foi retornado com êxito.|  
|{1&gt;E_FAIL&lt;1}|Não foi possível retornar o endereço do quadro interno.|  
|{1&gt;E_INVALIDARG&lt;1}|`pAddress` é `null`.|  
  
## <a name="remarks"></a>Comentários  
 O valor retornado em `pAddress` pode ser usado para determinar o local do quadro interno em relação a outros quadros na pilha. Mesmo em computadores baseados em IA-64, o quadro interno reside somente na pilha e não há nenhum ponteiro correspondente para um repositório de backup.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
