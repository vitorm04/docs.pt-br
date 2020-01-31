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
ms.openlocfilehash: bc33768e4155a0e272d3374d4c586c79ef2ff3fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792775"
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
 As chamadas para `SetIP` invalidam imediatamente todos os quadros e cadeias para o thread atual. Se o depurador precisar de informações de quadro após uma chamada para `SetIP`, ele deverá executar um novo rastreamento de pilha.  
  
 [ICorDebug](icordebug-interface.md) tentará manter o quadro de pilha em um estado válido. No entanto, mesmo que o quadro esteja em um estado válido, no que diz respeito ao tempo de execução, ainda pode haver problemas, como variáveis locais não inicializadas e assim por diante. O chamador é responsável por garantir a coerência do programa em execução.  
  
 Em plataformas de 64 bits, o ponteiro de instrução não pode ser movido para fora de um `catch` ou de um bloco de `finally`. Se `SetIP` for chamado para fazer essa movimentação em uma plataforma de 64 bits, ele retornará um HRESULT indicando falha.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também
