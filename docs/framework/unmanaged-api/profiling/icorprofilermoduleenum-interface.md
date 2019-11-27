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
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia desta `ICorProfilerModuleEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Obtém o número de módulos gerenciados que foram carregados no aplicativo.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Obtém o número especificado de módulos contíguos de uma coleção sequencial de objetos, começando na posição atual do enumerador na sequência.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Move o cursor do enumerador para a posição inicial da sequência.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Avança a posição do cursor do enumerador para que o número especificado de elementos seja ignorado.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorProfilerModuleEnum` é um enumerador. Ele permite que o destinatário de uma matriz Extraia elementos do remetente a uma taxa apropriada para o destinatário. Em outras palavras, o receptor é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando, assim, os problemas associados à passagem de matrizes grandes como parâmetros de método.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Método EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
