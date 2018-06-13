---
title: Método ICorDebugModule::IsDynamic
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5157c62f2719a9d62608750cd122561807197494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418286"
---
# <a name="icordebugmoduleisdynamic-method"></a>Método ICorDebugModule::IsDynamic
Obtém um valor que indica se esse módulo é dinâmico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDynamic`  
 [out] `true` se esse módulo é dinâmico; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Um módulo dinâmico pode adicionar novas classes e excluir as classes existentes, mesmo depois que o módulo foi carregado. O [: loadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) e [: Unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) retornos de chamada para informar o depurador quando uma classe foi adicionada ou excluída.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
