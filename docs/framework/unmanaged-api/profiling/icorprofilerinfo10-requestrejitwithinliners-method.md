---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c33a868b643cb3e3fd5dfaf436e3078bc590705c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449811"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>Método ICorProfilerInfo10:: RequestReJITWithInliners

ReJITs os métodos solicitados, bem como quaisquer inlineers dos métodos solicitados.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

#### <a name="parameters"></a>Parâmetros

`dwRejitFlags` \
no Um bitmask de [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).

`cFunctions` \
no O número de funções a serem recompiladas.

`moduleIds` \
no Especifica a parte `moduleId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.

`methodIds` \
no Especifica a parte `methodId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.

## <a name="remarks"></a>Comentários

O [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) não faz nenhum controle dos métodos embutidos. O criador de perfil era esperado para bloquear a inlinhação ou controlar o Intorno e chamar `RequestReJIT` para que todos os inlineers verifiquem se cada instância de um método embutido foi ReJITted. Isso representa um problema com o ReJIT na anexação, já que o criador de perfil não está presente para monitorar o inalinhamento. Esse método pode ser chamado para garantir que o conjunto completo de inlineers também será ReJITted.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
