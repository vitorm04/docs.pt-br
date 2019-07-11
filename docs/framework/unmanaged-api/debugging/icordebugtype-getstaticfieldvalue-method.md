---
title: Método ICorDebugType::GetStaticFieldValue
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1054c7c977a487bb5a4bbf464322a65bcc039608
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755739"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>Método ICorDebugType::GetStaticFieldValue
Obtém um ponteiro de interface para um objeto ICorDebugValue que contém o valor do campo estático referenciado pelo campo especificado token no quadro de pilha especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `fieldDef`  
 [in] Um `mdFieldDef` token que especifica o campo estático.  
  
 `pFrame`  
 [in] Um ponteiro para um ICorDebugFrame que representa o quadro de pilhas.  
  
 `ppValue`  
 [out] Um ponteiro para o endereço de um `ICorDebugValue` que contém o valor do campo estático.  
  
## <a name="remarks"></a>Comentários  
 O `GetStaticFieldValue` método pode ser usado somente se o tipo é ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, conforme indicado pelo [icordebugtype:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) método.  
  
 Para tipos não genéricos, a operação executada pelo `GetStaticFieldValue` é idêntico ao chamar [icordebugclass:: GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) no que é retornado pelo objeto ICorDebugClass [icordebugtype:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 Para tipos genéricos, o valor de um campo estático será em relação a uma instanciação específica. Além disso, se poderia ser o campo estático em relação a um thread, um contexto ou um domínio de aplicativo, em seguida, o quadro de pilha ajudará o depurador determinar o valor adequado.  
  
## <a name="remarks"></a>Comentários  
 `GetStaticFieldValue` pode ser usado apenas quando uma chamada para `ICorDebugType::GetType` retorna um valor de ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
