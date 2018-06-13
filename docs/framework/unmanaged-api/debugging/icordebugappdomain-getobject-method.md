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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f528bcef7d06b503b1ee9d7bd4a61d3d3e9672
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406514"
---
# <a name="icordebugappdomaingetobject-method"></a>Método ICorDebugAppDomain::GetObject
Obtém um ponteiro de interface para o domínio de aplicativo do common language runtime (CLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppObject`  
 [out] Um ponteiro para o endereço de um objeto de interface ICorDebugValue que representa o domínio do aplicativo CLR.  
  
## <a name="return-value"></a>Valor de retorno  
 Se um gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto ainda não foi construído para esse domínio de aplicativo, o método retorna `S_FALSE` e coloca `NULL` em `*ppObject`.  
  
## <a name="remarks"></a>Comentários  
 Cada domínio de aplicativo em um processo pode ter um gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto em tempo de execução que o representa. Esta função obtém um objeto de interface ICorDebugValue que corresponde a este gerenciado <xref:System.AppDomain?displayProperty=nameWithType> objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
