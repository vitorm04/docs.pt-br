---
title: Método ICorDebugAppDomain::EnumerateBreakpoints
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd7ee890a7f2c3ea8cd3de9fbe830575c0ca10c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402768"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a>Método ICorDebugAppDomain::EnumerateBreakpoints
Obtém um enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppBreakpoints`  
 [out] Um ponteiro para o endereço de um objeto de ICorDebugBreakpointEnum que é o enumerador para todos os pontos de interrupção ativos no domínio do aplicativo.  
  
## <a name="remarks"></a>Comentários  
 O enumerador inclui todos os tipos de pontos de interrupção, incluindo pontos de interrupção de função e os pontos de interrupção.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
