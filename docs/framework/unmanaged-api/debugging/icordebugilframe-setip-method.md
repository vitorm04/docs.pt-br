---
title: Método ICorDebugILFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 466fe421f4ff3f8983159ccb38503b75551c87bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788553"
---
# <a name="icordebugilframesetip-method"></a>Método ICorDebugILFrame::SetIP
Define o ponteiro de instrução para o local de deslocamento especificado no código MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `nOffset`  
 O local de deslocamento no código MSIL.  
  
## <a name="remarks"></a>Comentários  
 As chamadas para `SetIP` invalidam imediatamente todos os quadros e cadeias para o thread atual. Se o depurador precisar de informações de quadro após uma chamada para `SetIP`, ele deverá executar um novo rastreamento de pilha.  
  
 [ICorDebug](icordebug-interface.md) tentará manter o quadro de pilha em um estado válido. No entanto, mesmo que o quadro esteja em um estado válido, ainda pode haver problemas como variáveis locais não inicializadas. O chamador é responsável por garantir a coerência do programa em execução.  
  
 Em plataformas de 64 bits, o ponteiro de instrução não pode ser movido para fora de um `catch` ou de um bloco de `finally`. Se `SetIP` for chamado para fazer essa movimentação em uma plataforma de 64 bits, ele retornará um HRESULT indicando falha.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
