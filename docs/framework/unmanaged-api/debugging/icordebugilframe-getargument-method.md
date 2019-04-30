---
title: Método ICorDebugILFrame::GetArgument
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46852ed8ac53c3a7720edff4833f3dc3cce42bbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995521"
---
# <a name="icordebugilframegetargument-method"></a>Método ICorDebugILFrame::GetArgument
Obtém o valor do argumento especificado neste quadro de pilha Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwIndex`  
 [in] O índice do argumento deste quadro de pilhas MSIL.  
  
 `ppValue`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor recuperado.  
  
## <a name="remarks"></a>Comentários  
 O `GetArgument` método pode ser usado em um quadro de pilha MSIL ou em um quadro de compilado just-in-time (JIT).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
