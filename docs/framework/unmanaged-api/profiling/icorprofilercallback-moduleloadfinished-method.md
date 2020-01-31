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
ms.openlocfilehash: 661229e5fbd5d106662f0e823a1753bd76c33311
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866163"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>Método ICorProfilerCallback::ModuleLoadFinished
Notifica o criador de perfil que concluiu o carregamento de um módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no A ID do módulo que concluiu o carregamento.  
  
 `hrStatus`  
 no Um HRESULT que indica se o módulo foi carregado com êxito.  
  
## <a name="remarks"></a>Comentários  
 O valor de `moduleId` não é válido para uma solicitação de informações até que o método `ModuleLoadFinished` seja chamado.  
  
 Algumas partes do carregamento do módulo podem continuar depois do `ModuleLoadFinished` retorno de chamada. Uma falha HRESULT no `hrStatus` indica uma falha. No entanto, um HRESULT de êxito em `hrStatus` indica apenas que a primeira parte do carregamento do módulo foi bem-sucedida.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerCallback](icorprofilercallback-interface.md)
- [Método ModuleLoadStarted](icorprofilercallback-moduleloadstarted-method.md)
