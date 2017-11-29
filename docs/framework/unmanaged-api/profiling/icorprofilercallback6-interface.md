---
title: Interface ICorProfilerCallback6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dca83aca3aee4a072e90793e1bb33526b6e5ebd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback6-interface"></a>Interface ICorProfilerCallback6
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Uma subclasse de [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) que fornece um método de retorno de chamada que usa o common language runtime para notificar um criador de perfil que está carregando um assembly.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|Notifica o criador de perfis de que um assembly está em um estágio inicial de carregamento, quando o Common Language Runtime realiza um exame de fechamento da referência do assembly.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
