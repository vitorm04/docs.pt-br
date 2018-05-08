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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0017cff43f7a1b1bdd90806f50abb374a96dadf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>Método ICorProfilerCallback::AppDomainCreationFinished
Notifica o criador de perfil que foi criado um domínio de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `appDomainId`  
 [in] Identifica o domínio que foi criado.  
  
 `hrStatus`  
 [in] Um HRESULT que indica se a criação do domínio do aplicativo foi concluída com êxito.  
  
## <a name="remarks"></a>Comentários  
 A ID do aplicativo não é válida para qualquer solicitação de informações até que o `AppDomainCreationFinished` método é chamado.  
  
 Algumas partes do carregamento de domínio do aplicativo podem continuar após o `AppDomainCreationFinished` retorno de chamada. Uma falha de HRESULT em `hrStatus` indica uma falha. No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte da criação do domínio de aplicativo foi bem-sucedida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
