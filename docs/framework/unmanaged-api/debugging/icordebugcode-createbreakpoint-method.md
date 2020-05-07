---
title: Método ICorDebugCode::CreateBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
ms.openlocfilehash: 40582b1289875d5151ea96e3153c6e4760737e84
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893803"
---
# <a name="icordebugcodecreatebreakpoint-method"></a>Método ICorDebugCode::CreateBreakpoint
Cria um ponto de interrupção neste segmento de código no deslocamento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `offset`  
 no O deslocamento no qual criar o ponto de interrupção.  
  
 `ppBreakpoint`  
 fora Um ponteiro para o endereço de um objeto "ICorDebugFunctionBreakpoint" que representa o ponto de interrupção.  
  
## <a name="remarks"></a>Comentários  
 Antes que o ponto de interrupção esteja ativo, ele deve ser adicionado ao objeto de processo.  
  
 Se esse código for um código MSIL (Microsoft Intermediate Language) e houver uma versão nativa compilada JIT (just-in-time) do código, o ponto de interrupção será aplicado também no código compilado por JIT. (O mesmo será verdadeiro se o código for compilado em JIT posteriormente.)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
