---
title: "Método ICorProfilerCallback::AppDomainShutdownFinished"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 443f5cd48693d6ac3ce732746666bd2d5e3786fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>Método ICorProfilerCallback::AppDomainShutdownFinished
Notifica o criador de perfil que um domínio de aplicativo foi descarregado de um processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `appDomainId`  
 [in] Identifica o domínio em que os assemblies do aplicativo são armazenados.  
  
 `hrStatus`  
 [in] Um HRESULT que indica se o domínio de aplicativo foi descarregado com êxito.  
  
## <a name="remarks"></a>Comentários  
 O valor de `appDomainId` não é válido para uma solicitação de informações após o [: Appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) método retorna.  
  
 Algumas partes do descarregar o domínio de aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada. Uma falha de HRESULT em `hrStatus` indica uma falha. No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do descarregar o domínio de aplicativo foi bem-sucedida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
