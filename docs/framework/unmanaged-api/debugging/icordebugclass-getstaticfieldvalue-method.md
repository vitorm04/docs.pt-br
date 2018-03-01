---
title: "Método ICorDebugClass::GetStaticFieldValue"
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
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 21176eb73b3655fe8bd4b2187b6da49a3c31bd82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a>Método ICorDebugClass::GetStaticFieldValue
Obtém o valor do campo estático especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fieldDef`  
 [in] Um campo `Def` token que referencia o campo a ser recuperado.  
  
 `pFrame`  
 [in] Um ponteiro para um objeto ICorDebugFrame que representa o quadro a ser usado para resolver a ambiguidade entre threads, contexto ou estáticos de domínio de aplicativo.  
  
 Se o campo estático é em relação a um thread, um contexto ou um domínio de aplicativo, o quadro determinará o valor adequado.  
  
 `ppValue`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do campo estático.  
  
## <a name="remarks"></a>Comentários  
 Para tipos parametrizados, o valor de um campo estático é relativo a instanciação específica. Portanto, se o construtor de classe aceitar parâmetros de tipo <xref:System.Type>, chame [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) em vez de `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
