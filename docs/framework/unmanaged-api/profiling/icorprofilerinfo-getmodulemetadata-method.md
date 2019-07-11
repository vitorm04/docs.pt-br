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
ms.openlocfilehash: 2e63cf698e41e70084c9b71bdf58d7ac60723d53
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782784"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>Método ICorProfilerInfo::GetModuleMetaData
Obtém uma instância de interface de metadados que é mapeado para o módulo especificado.  
  
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
 [in] A ID do módulo ao qual a instância da interface será mapeada.  
  
 `dwOpenFlags`  
 [in] Um valor igual a [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeração que especifica o modo para abrir arquivos de manifesto. Somente o `ofRead`, `ofWrite` e `ofNoTransform` bits são válidos.  
  
 `riid`  
 [in] A referência de ID (GUID) da interface de metadados cuja instância será recuperada. Ver [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) para obter uma lista das interfaces.  
  
 `ppOut`  
 [out] Um ponteiro para o endereço da instância de interface de metadados.  
  
## <a name="remarks"></a>Comentários  
 Você pode solicitar que os metadados a ser aberto no modo de leitura/gravação, mas isso resulta em execução mais lenta de metadados do programa, porque as alterações feitas para os metadados não podem ser otimizados como estavam do compilador.  
  
 Alguns módulos (por exemplo, os módulos de recursos) não têm nenhum metadado. Nesses casos, `GetModuleMetaData` retornará um valor HRESULT S_FALSE e um valor nulo em *`ppOut`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
