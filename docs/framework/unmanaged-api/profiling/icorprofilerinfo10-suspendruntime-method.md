---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8d00718579f44a164cd83e2b05d41f70f1c65785
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452143"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a>Método ICorProfilerInfo10:: SuspendRuntime

Suspende o tempo de execução sem executar um GC.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
