---
title: Método ICorProfilerCallback::AssemblyUnloadFinished
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6a9fe86d6160ebac084625ef94013cce9a27a3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501874"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>Método ICorProfilerCallback::AssemblyUnloadFinished
Notifica o criador de perfil que um assembly foi descarregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `assemblyId`  
 [in] Identifica o assembly que está sendo descarregado.  
  
 `hrStatus`  
 [in] Um HRESULT que indica se o assembly foi descarregado com êxito.  
  
## <a name="remarks"></a>Comentários  
 O valor de `assemblyId` não é válido para uma solicitação de informações após a [ICorProfilerCallback:: Assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) retorno do método.  
  
 Algumas partes de descarregar o assembly podem continuar após o `AssemblyUnloadFinished` retorno de chamada. Uma falha HRESULT em `hrStatus` indica uma falha. No entanto, um HRESULT de sucesso em `hrStatus` indica apenas que a primeira parte de descarregar o assembly foi bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
