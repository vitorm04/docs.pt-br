---
title: Método ICorProfilerCallback::AppDomainShutdownStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: d280b008b34befce04159d02dfbb3de37b262c3c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866657"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a>Método ICorProfilerCallback::AppDomainShutdownStarted
Notifica o criador de perfil de que um domínio de aplicativo está sendo descarregado de um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a>Parâmetros

- `appDomainId`

  \[em] identifica o domínio no qual os assemblies do aplicativo são armazenados.

## <a name="remarks"></a>Comentários  
 O valor de `appDomainId` não é válido para nenhuma solicitação de informações após o retorno do método `AppDomainShutdownStarted` — essa é a última chance do criador de perfil obter informações sobre esse domínio de aplicativo.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
