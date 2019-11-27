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
ms.openlocfilehash: c7bf8e3ebedb17a4536b604909434c3e004fc828
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439832"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>Método ICorProfilerInfo::GetModuleMetaData
Obtém uma instância de interface de metadados que mapeia para o módulo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no A ID do módulo para o qual a instância de interface será mapeada.  
  
 `dwOpenFlags`  
 no Um valor da enumeração [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) que especifica o modo para abrir arquivos de manifesto. Somente os bits `ofRead`, `ofWrite` e `ofNoTransform` são válidos.  
  
 `riid`  
 no A ID de referência (GUID) da interface de metadados cuja instância será recuperada. Consulte [interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) para obter uma lista das interfaces.  
  
 `ppOut`  
 fora Um ponteiro para o endereço da instância da interface de metadados.  
  
## <a name="remarks"></a>Comentários  
 Você pode solicitar que os metadados sejam abertos no modo de leitura/gravação, mas isso resultará em uma execução de metadados mais lenta do programa, pois as alterações feitas nos metadados não podem ser otimizadas como eram do compilador.  
  
 Alguns módulos (como módulos de recurso) não têm metadados. Nesses casos, `GetModuleMetaData` retornará um valor HRESULT de S_FALSE e um nulo em *`ppOut`.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
