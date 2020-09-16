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
ms.openlocfilehash: e3d5a09730cb8e477bd506749017a403acff1696
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540550"
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

## <a name="parameters"></a>Parâmetros

- `dwRejitFlags`

  \[in] um bitmask de [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).

- `cFunctions`

  \[in] o número de funções a serem recompiladas.

- `moduleIds`

  \[in] Especifica a `moduleId` parte dos pares ( `module` , `methodDef` ) que identificam as funções a serem recompiladas.

- `methodIds`

  \[in] Especifica a `methodId` parte dos pares ( `module` , `methodDef` ) que identificam as funções a serem recompiladas.

## <a name="remarks"></a>Comentários

O [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) não faz nenhum controle dos métodos embutidos. O criador de perfil era esperado para bloquear a linhagem ou controlar a inlinhação e chamar `RequestReJIT` todos os inlineers para garantir que cada instância de um método embutido fosse ReJITted. Isso representa um problema com o ReJIT na anexação, já que o criador de perfil não está presente para monitorar o inalinhamento. Esse método pode ser chamado para garantir que o conjunto completo de inlineers também será ReJITted.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
