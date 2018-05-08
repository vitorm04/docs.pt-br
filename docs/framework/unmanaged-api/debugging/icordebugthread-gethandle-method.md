---
title: Método ICorDebugThread::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 358597edc9fbc5203e5c00a5fb4d04019281060d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadgethandle-method"></a>Método ICorDebugThread::GetHandle
Obtém o identificador atual para a parte ativa deste ICorDebugThread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `phThreadHandle`  
 [out] Um ponteiro para um HTHREAD que é o identificador da parte ativa desse thread.  
  
## <a name="remarks"></a>Comentários  
 O identificador pode alterar como o processo é executado e pode ser diferente para diferentes partes do thread.  
  
 Esse identificador é de propriedade pela API de depuração. O depurador deve duplicar antes de usá-lo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
