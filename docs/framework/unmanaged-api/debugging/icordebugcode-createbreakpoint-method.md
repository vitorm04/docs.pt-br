---
title: "Método ICorDebugCode::CreateBreakpoint"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 211435025fe06eff180244430138be9d42c5eb86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 
