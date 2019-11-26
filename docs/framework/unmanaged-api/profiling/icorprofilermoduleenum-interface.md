---
title: Interface ICorProfilerModuleEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 5c4efff46c2460ee77f5a8011dc80796ac62a69e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442701"
---
# <a name="icorprofilermoduleenum-interface"></a>Interface ICorProfilerModuleEnum
Fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos carregados pelo aplicativo ou pelo criador de perfis.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Gets the number of managed modules that were loaded into the application.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Moves the enumerator's cursor to the starting position of the sequence.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Advances the position of the enumerator's cursor so that the specified number of elements are skipped.|  
  
## <a name="remarks"></a>Comentários  
 The `ICorProfilerModuleEnum` interface is an enumerator. It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver. In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Método EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
