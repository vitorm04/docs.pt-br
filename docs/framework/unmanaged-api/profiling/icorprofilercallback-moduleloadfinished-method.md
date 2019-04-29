---
title: Método ICorProfilerCallback::ModuleLoadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 354d2f278bcb0618b823b7300079278fc4c3315c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758477"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>Método ICorProfilerCallback::ModuleLoadFinished
Notifica o criador de perfil de um módulo terminou o carregamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] A ID do módulo que concluiu o carregamento.  
  
 `hrStatus`  
 [in] Um HRESULT que indica se o módulo foi carregado com êxito.  
  
## <a name="remarks"></a>Comentários  
 O valor de `moduleId` não é válido para uma solicitação de informações até que o `ModuleLoadFinished` método é chamado.  
  
 Algumas partes de carregar o módulo podem continuar após o `ModuleLoadFinished` retorno de chamada. Uma falha HRESULT em `hrStatus` indica uma falha. No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte do módulo de carregamento foi bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método ModuleLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
