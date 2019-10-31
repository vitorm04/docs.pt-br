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
ms.openlocfilehash: cff527aa7cde6a13667d47d030a0ef7db96ad5ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122339"
---
# <a name="icordebugtypegetbase-method"></a>Método ICorDebugType::GetBase
Obtém um ponteiro de interface para um ICorDebugType que representa o tipo base, se houver um, do tipo representado por esse `ICorDebugType`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pBase`  
 fora Um ponteiro para o endereço de um objeto de `ICorDebugType` que representa o tipo base.  
  
## <a name="remarks"></a>Comentários  
 Pesquisar o tipo base de um tipo é útil para implementar a funcionalidade comum do depurador, como imprimir todos os campos de um objeto ou suas classes pai.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
