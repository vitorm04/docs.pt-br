---
title: Interface ICorProfilerObjectEnum
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92370751b38029435b12c177b75cd4d9402369b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220936"
---
# <a name="icorprofilerobjectenum-interface"></a>Interface ICorProfilerObjectEnum
Fornece métodos para iterar em uma coleção de objetos congelados que são gerados pelo sequencialmente os [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Obtém um ponteiro de interface para uma cópia deste `ICorProfilerObjectEnum` interface.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Obtém o número total de objetos congelados na coleção.|  
|[Método Next](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Obtém o número especificado de objetos contíguos de uma coleção sequencial de objetos, começando na posição atual na sequência do enumerador.|  
|[Método Reset](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Move o cursor deste enumerador para a posição inicial da sequência.|  
|[Método Skip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Avança o cursor este enumerador de sua posição atual para que o número especificado de elementos é ignorado.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorProfilerObjectEnum` interface é um enumerador. Ele permite que o destinatário de uma matriz a elementos de pull do remetente de uma taxa que é apropriado para o receptor. Em outras palavras, o destinatário é capaz de controlar explicitamente o fluxo de elementos de matriz, evitando assim os problemas relacionados ao passar matrizes grandes como parâmetros de método.  
  
 Use [ICorProfilerInfo2::EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) para obter um ponteiro para o `ICorProfilerObjectEnum` interface.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Método EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
