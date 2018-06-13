---
title: Método ICorDebugNativeFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed8b6bf60790c10b9869dcc41678be050b8979dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420219"
---
# <a name="icordebugnativeframesetip-method"></a>Método ICorDebugNativeFrame::SetIP
Define o ponteiro de instrução para o local de deslocamento especificado em código nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nOffset`  
 [in] O local de deslocamento no código nativo.  
  
## <a name="remarks"></a>Comentários  
 Chamadas para `SetIP` imediatamente invalida todos os quadros e cadeias de para o thread atual. Se o depurador precisa de informações de quadro após uma chamada para `SetIP`, ele deve realizar um novo rastreamento de pilha.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) tentará manter o quadro de pilha em um estado válido. No entanto, mesmo se o quadro estiver em um estado válido, que diz respeito o tempo de execução, ainda pode haver problemas, como variáveis locais não inicializadas e assim por diante. O chamador é responsável por garantir a coerência do programa em execução.  
  
 Em plataformas de 64 bits, o ponteiro de instrução não pode ser movido de um `catch` ou `finally` bloco. Se `SetIP` é chamado para fazer isso em uma plataforma de 64 bits, será retornado um HRESULT indicando falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
