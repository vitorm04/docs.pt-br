---
title: Método ICorProfilerInfo::BeginInprocDebugging
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82e798e1a31f771c63e71f2a85f8cbb684b237bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>Método ICorProfilerInfo::BeginInprocDebugging
Inicializa suporte à depuração no processo. Este método está obsoleto no .NET Framework versão 2.0.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fThisThreadOnly`  
 [in] Defina esse valor como `true` para inicializar o suporte à depuração somente do thread atual; defina-a como `false` para inicializar o suporte à depuração de todos os threads.  
  
 `pdwProfilerContext`  
 [out] O ponteiro para um valor retornado que identifica a sessão de depuração.  
  
## <a name="remarks"></a>Comentários  
 Os serviços de depuração do CLR tem suporte limitado depuração em andamento nas versões do .NET Framework 1.0 e 1.1. No processo de depuração habilitado um criador de perfil usar as partes de inspeção da API de depuração. No entanto, devido a comentários dos clientes, no processo de depuração foi removido do .NET Framework versão 2.0 e substituído por um conjunto de funcionalidades mais alinhados com a API de criação de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versão do .NET framework:** 1.0  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
