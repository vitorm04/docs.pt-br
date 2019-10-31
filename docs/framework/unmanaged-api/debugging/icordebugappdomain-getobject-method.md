---
title: Método ICorDebugAppDomain::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetObject
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type:
- apiref
ms.openlocfilehash: f2c881603cfa0e4b3d2dc8d1e996631b51d1e850
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134709"
---
# <a name="icordebugappdomaingetobject-method"></a>Método ICorDebugAppDomain::GetObject
Obtém um ponteiro de interface para o domínio do aplicativo Common Language Runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppObject`  
 fora Um ponteiro para o endereço de um objeto de interface ICorDebugValue que representa o domínio do aplicativo CLR.  
  
## <a name="return-value"></a>Valor retornado  
 Se um objeto <xref:System.AppDomain?displayProperty=nameWithType> gerenciado não tiver sido construído para esse domínio de aplicativo, o método retornará `S_FALSE` e colocará `NULL` em `*ppObject`.  
  
## <a name="remarks"></a>Comentários  
 Cada domínio de aplicativo em um processo pode ter um objeto <xref:System.AppDomain?displayProperty=nameWithType> gerenciado no tempo de execução que o representa. Essa função obtém um objeto de interface ICorDebugValue que corresponde a esse objeto de <xref:System.AppDomain?displayProperty=nameWithType> gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
