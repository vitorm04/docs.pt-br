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
ms.openlocfilehash: 786c0e7b38c74fd02dd6f7536af1899f295b0305
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206450"
---
# <a name="icordebugnativeframesetip-method"></a>Método ICorDebugNativeFrame::SetIP
Define o ponteiro de instrução para o local de deslocamento especificado no código nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `nOffset`  
 no O local de deslocamento no código nativo.  
  
## <a name="remarks"></a>Comentários  
 As chamadas para `SetIP` invalidar imediatamente todos os quadros e cadeias para o thread atual. Se o depurador precisar de informações de quadro após uma chamada para `SetIP` , ele deverá executar um novo rastreamento de pilha.  
  
 [ICorDebug](icordebug-interface.md) tentará manter o quadro de pilha em um estado válido. No entanto, mesmo que o quadro esteja em um estado válido, no que diz respeito ao tempo de execução, ainda pode haver problemas, como variáveis locais não inicializadas e assim por diante. O chamador é responsável por garantir a coerência do programa em execução.  
  
 Em plataformas de 64 bits, o ponteiro de instrução não pode ser movido para fora de um `catch` `finally` bloco ou. Se `SetIP` for chamado para fazer uma movimentação desse tipo em uma plataforma de 64 bits, ele retornará um HRESULT indicando falha.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também
