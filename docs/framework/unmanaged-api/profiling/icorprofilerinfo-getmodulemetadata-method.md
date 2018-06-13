---
title: Método ICorProfilerInfo::GetModuleMetaData
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2491b700e8fac512f0d782a42e30ae3114e93c3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455530"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>Método ICorProfilerInfo::GetModuleMetaData
Obtém uma instância da interface de metadados que é mapeado para o módulo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] A ID do módulo ao qual a instância da interface será mapeada.  
  
 `dwOpenFlags`  
 [in] Um valor de [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeração que especifica o modo para abrir arquivos de manifesto. Somente o `ofRead`, `ofWrite` e `ofNoTransform` bits são válidos.  
  
 `riid`  
 [in] A referência de ID (GUID) da interface de metadados cuja instância será recuperada. Consulte [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) para obter uma lista das interfaces.  
  
 `ppOut`  
 [out] Um ponteiro para o endereço da instância de interface de metadados.  
  
## <a name="remarks"></a>Comentários  
 Você pode solicitar os metadados a ser aberto no modo de leitura/gravação, mas isso resultará em execução mais lenta de metadados do programa, alterações feitas em metadados não podem ser otimizados como estavam do compilador.  
  
 Alguns módulos (por exemplo, os módulos de recurso) não tem nenhum metadado. Nesses casos, `GetModuleMetaData` retornará um valor HRESULT S_FALSE e um valor nulo em *`ppOut`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
