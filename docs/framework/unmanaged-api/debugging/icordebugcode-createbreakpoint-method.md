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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1173091a5f2d8814747c93f827150afe39b8b309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcodecreatebreakpoint-method"></a>Método ICorDebugCode::CreateBreakpoint
Cria um ponto de interrupção neste segmento de código no deslocamento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `offset`  
 [in] O deslocamento no qual criar o ponto de interrupção.  
  
 `ppBreakpoint`  
 [out] Um ponteiro para o endereço de um objeto de "ICorDebugFunctionBreakpoint" que representa o ponto de interrupção.  
  
## <a name="remarks"></a>Comentários  
 Antes do ponto de interrupção está ativo, ele deve ser adicionado ao objeto de processo.  
  
 Se esse código é código Microsoft intermediate language (MSIL) e há um just-in-time (JIT)-versão nativo compilado do código, o ponto de interrupção será aplicado o código de compilação JIT. (O mesmo é verdadeiro se o código de compilação JIT posteriormente.)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
