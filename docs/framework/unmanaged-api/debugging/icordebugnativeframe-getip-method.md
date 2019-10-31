---
title: Método ICorDebugNativeFrame::GetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: 3011a8c7e5cf278768587633967b2e9491cf87ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137329"
---
# <a name="icordebugnativeframegetip-method"></a>Método ICorDebugNativeFrame::GetIP
Obtém o local de deslocamento de código nativo para o qual o ponteiro de instrução está definido no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pnOffset`  
 fora Um ponteiro para o local de deslocamento no código nativo.  
  
## <a name="remarks"></a>Comentários  
 Se o registro de ativação representado por esse "ICorDebugNativeFrame" estiver ativo, o deslocamento será o endereço da próxima instrução a ser executada. Se esse quadro de pilhas não estiver ativo, o deslocamento será o endereço da próxima instrução a ser executada quando o registro de ativação for reativado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
