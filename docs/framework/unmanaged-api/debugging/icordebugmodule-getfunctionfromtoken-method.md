---
title: Método ICorDebugModule::GetFunctionFromToken
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1af0f8f792c856c0b27b4d3d9ff557bcc5fce82
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500064"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>Método ICorDebugModule::GetFunctionFromToken
Obtém a função que é especificada pelo token de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `methodDef`  
 [in] Um `mdMethodDef` token de metadados que faz referência a metadados da função.  
  
 `ppFunction`  
 [out] Um ponteiro para o endereço de um objeto de interface ICorDebugFunction que representa a função.  
  
## <a name="remarks"></a>Comentários  
 O `GetFunctionFromToken` método retorna um HRESULT CORDBG_E_FUNCTION_NOT_IL se o valor passado em `methodDef` não faz referência a um método do Microsoft intermediate language (MSIL).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
