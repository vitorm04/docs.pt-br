---
title: Método ICorDebugType::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff2258faa8bc766c8c769f4e135f868334516b96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422553"
---
# <a name="icordebugtypegetclass-method"></a>Método ICorDebugType::GetClass
Obtém um ponteiro de interface para um ICorDebugClass que representa o tipo genérico instanciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppClass`  
 [out] Um ponteiro para o endereço de um `ICorDebugClass` interface que representa o tipo genérico instanciado.  
  
## <a name="remarks"></a>Comentários  
 `GetClass` pode ser chamado apenas em determinadas condições. Chamar [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) antes de chamar `GetClass`. Se `ICorDebugType::GetType` retorna um valor de CorElementType ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, `GetClass` pode ser chamado para obter o tipo instanciado para um tipo genérico.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
