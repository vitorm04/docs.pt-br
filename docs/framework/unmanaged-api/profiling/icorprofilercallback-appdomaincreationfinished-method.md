---
title: Método ICorProfilerCallback::AppDomainCreationFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177066"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>Método ICorProfilerCallback::AppDomainCreationFinished
Notifica o profiler de que um domínio de aplicativo foi criado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a>parâmetros

- `appDomainId`

  \[em] Identifica o domínio que foi criado.

- `hrStatus`

  \[em] Um HRESULT que indica se a criação do domínio do aplicativo foi concluída com sucesso.

## <a name="remarks"></a>Comentários  
 O ID do aplicativo não é `AppDomainCreationFinished` válido para qualquer solicitação de informação até que o método seja chamado.  
  
 Algumas partes do carregamento do `AppDomainCreationFinished` domínio do aplicativo podem continuar após o retorno de chamada. Uma falha hresult em `hrStatus` indica uma falha. No entanto, um `hrStatus` HRESULT de sucesso indica apenas que a primeira parte da criação do domínio do aplicativo foi bem sucedida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
