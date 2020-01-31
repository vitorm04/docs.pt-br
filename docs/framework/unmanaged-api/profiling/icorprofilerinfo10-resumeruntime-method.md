---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 49de3383902791b1278e7c9221a80c3454eb12a2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868914"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a>Método ICorProfilerInfo10:: ResumeRuntime

Retoma o tempo de execução sem executar um GC.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a>Requisitos do

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
