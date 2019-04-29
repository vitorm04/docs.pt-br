---
title: Método ICorDebugClass::GetStaticFieldValue
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b67f5ec233679461f61715d7562b47c2a195fb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750845"
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
  
## <a name="parameters"></a>Parâmetros  
 `fieldDef`  
 [in] Um campo `Def` token que referencia o campo a ser recuperado.  
  
 `pFrame`  
 [in] Um ponteiro para um objeto de ICorDebugFrame que representa o quadro a ser usado para resolver a ambiguidade entre threads, contexto ou estáticos de domínio do aplicativo.  
  
 Se o campo estático é em relação a um thread, um contexto ou um domínio de aplicativo, o quadro determina o valor adequado.  
  
 `ppValue`  
 [out] Um ponteiro para o endereço de um objeto ICorDebugValue que representa o valor do campo estático.  
  
## <a name="remarks"></a>Comentários  
 Para tipos parametrizados, o valor de um campo estático é em relação a instanciação específica. Portanto, se o construtor da classe usa parâmetros do tipo <xref:System.Type>, chame [icordebugtype:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md) em vez de `ICorDebugClass::GetStaticFieldValue`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
