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
ms.openlocfilehash: 37bf5abf66b613d8432af84c7d73aff60e9127cb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791267"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>Método ICorDebugType::GetStaticFieldValue
Obtém um ponteiro de interface para um objeto ICorDebugValue que contém o valor do campo estático referenciado pelo token de campo especificado no quadro de ativação especificado.  
  
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
 no Um token `mdFieldDef` que especifica o campo estático.  
  
 `pFrame`  
 no Um ponteiro para um ICorDebugFrame que representa o quadro de pilha.  
  
 `ppValue`  
 fora Um ponteiro para o endereço de um `ICorDebugValue` que contém o valor do campo estático.  
  
## <a name="remarks"></a>Comentários  
 O método `GetStaticFieldValue` pode ser usado somente se o tipo for ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, conforme indicado pelo método [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
 Para tipos não genéricos, a operação executada por `GetStaticFieldValue` é idêntica à chamada de [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) no objeto ICorDebugClass retornado por [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).  
  
 Para tipos genéricos, um valor de campo estático será relativo a uma instanciação específica. Além disso, se o campo estático puder ser relativo a um thread, um contexto ou um domínio de aplicativo, o quadro de pilha ajudará o depurador a determinar o valor adequado.  
  
## <a name="remarks"></a>Comentários  
 `GetStaticFieldValue` pode ser usado somente quando uma chamada para `ICorDebugType::GetType` retorna um valor de ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
