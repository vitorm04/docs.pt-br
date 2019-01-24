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
ms.openlocfilehash: f7bfdcc3c8328d71146732fc4ba5664ebee9bea2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574866"
---
# <a name="icordebugmoduleisinmemory-method"></a>Método ICorDebugModule::IsInMemory
Obtém um valor que indica se este módulo existe apenas na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
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


