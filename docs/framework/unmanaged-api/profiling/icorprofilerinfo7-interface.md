---
title: Interface ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786237"
---
# <a name="icorprofilerinfo7-interface"></a>Interface ICorProfilerInfo7
[Com suporte no [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] e versões posteriores]  
  
 Uma subclasse de [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) que fornece um método para aplicar recentemente definido metadados para um módulo e que fornece acesso a um fluxo de símbolo na memória.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ApplyMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|Aplica-se os metadados recentemente definido pelo `IMetadataEmit::Define*` métodos para um módulo especificado.|  
|[Método GetInMemorySymbolsLength](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|Retorna o comprimento de um fluxo de símbolo na memória.|  
|[ReadInMemorySymbols](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|Lê os bytes do fluxo símbolo na memória.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
