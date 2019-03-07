---
title: Método ICorDebugType::GetBase
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d04bc67013a2227f295ac3a41be027b9f9b04e2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478720"
---
# <a name="icordebugtypegetbase-method"></a>Método ICorDebugType::GetBase
Obtém um ponteiro de interface para um que representa o tipo base, se houver, do tipo representado por este ICorDebugType `ICorDebugType`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pBase`  
 [out] Um ponteiro para o endereço de um `ICorDebugType` objeto que representa o tipo base.  
  
## <a name="remarks"></a>Comentários  
 Procurar o tipo base para um tipo é útil para implementar a funcionalidade comum do depurador, como a impressão de todos os campos de um objeto ou suas classes pai.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
