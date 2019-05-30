---
title: Interface ICorProfilerInfo7
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a734bfdef89d4f8f9459f49a3ce2cee83faef9f6
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66250982"
---
# <a name="icorprofilerinfo7-interface"></a>Interface ICorProfilerInfo7
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
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
