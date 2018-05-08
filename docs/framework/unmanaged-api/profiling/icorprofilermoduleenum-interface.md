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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2275eb37d0e62c3f0ee8bbc8ea6db66901a3f1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilermoduleenum-interface"></a>Interface ICorProfilerModuleEnum
Fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos carregados pelo aplicativo ou pelo criador de perfis.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia deste `ICorProfilerModuleEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Obtém o número de módulos gerenciados que foram carregados no aplicativo.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Obtém o número especificado de contíguos módulos de uma coleção sequencial de objetos, a posição atual do enumerador na sequência.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Move o cursor do enumerador para a posição inicial da sequência de.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Avança a posição do cursor do enumerador para que o número especificado de elementos será ignorado.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorProfilerModuleEnum` interface é um enumerador. Ele permite que o destinatário de uma matriz para elementos de pull do remetente a uma taxa que é apropriado para o receptor. Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos da matriz, evitando, assim, os problemas associados à transmitindo matrizes grandes como parâmetros de método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Método EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
