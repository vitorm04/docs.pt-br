---
title: Método ICorDebugModule::IsInMemory
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79a8b0c3c56ffe2b8f57ec26f5942ee0d681194
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187584"
---
# <a name="icordebugmoduleisinmemory-method"></a>Método ICorDebugModule::IsInMemory
Obtém um valor que indica se este módulo existe apenas na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pInMemory`  
 [out] `true` se esse módulo existe apenas na memória; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 O common language runtime (CLR) dá suporte o carregamento de módulos de brutos fluxos de bytes. Esses módulos são chamados *módulos de memória* e não existem no disco.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
