---
title: Interface ICorProfilerInfo6
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: 80ac17a96e5c1c8c32cfc336da6c2be30eaf80fd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868363"
---
# <a name="icorprofilerinfo6-interface"></a>Interface ICorProfilerInfo6
[Com suporte no .NET Framework 4,6 e versões posteriores]  
  
 Uma subclasse de [ICorProfilerInfo5](icorprofilerinfo5-interface.md) que fornece um enumerador para todos os métodos que são definidos em um determinado módulo NGen e embutidos em um determinado método.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|Retorna um enumerador para todos os métodos que pertencem a um determinado módulo NGen e que são embutidos no corpo de um determinado método.|  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
