---
title: Interface ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: 655cdd5db0894a4e44d43b071caf1ee0829ffe50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861717"
---
# <a name="icorprofilerinfo5-interface"></a>Interface ICorProfilerInfo5
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Uma subclasse de [ICorProfilerInfo4](icorprofilerinfo4-interface.md) que fornece métodos para uso por infilers de código para se comunicar com o Common Language Runtime (CLR) para controlar o monitoramento de eventos.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetEventMask2](icorprofilerinfo5-geteventmask2-method.md)|Obtém as categorias de eventos atuais para os quais o criador de perfis deseja receber notificações do CLR.|  
|[Método SetEventMask2](icorprofilerinfo5-seteventmask2-method.md)|Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber notificações de evento do CLR.|  
  
## <a name="remarks"></a>Comentários  
 Os métodos disponíveis nesta interface destinam-se a substituir os métodos [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) e [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
