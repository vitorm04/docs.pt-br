---
title: Interface ICorProfilerCallback5
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 7981e7d2d2a4588e56d3c30d0ede2d003fdcd32e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865019"
---
# <a name="icorprofilercallback5-interface"></a>Interface ICorProfilerCallback5
Complementa as informações para ajudar um criador de perfil a identificar o fechamento completo de objetos dinâmicos, quando usado com o método [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) ou [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) junto com os métodos [ICorProfilerCallback:: objectreferenciations](icorprofilercallback-objectreferences-method.md) e [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .  
  
 O `ICorProfilerCallback5` deve ser implementado por um criador de perfil de memória gerenciada para assinar as notificações relacionadas aos identificadores dependentes.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|Identifica o fechamento transitivo de objetos referenciados por estas raízes por meio de referências diretas do campo de membro e de dependências `ConditionalWeakTable`.|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Interface ICorProfilerCallback2](icorprofilercallback2-interface.md)
