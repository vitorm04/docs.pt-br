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
ms.openlocfilehash: 99b6893854c358720259095bf3c0270cb3676483
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452169"
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

## <a name="parameters"></a>parâmetros

- `dwRejitFlags`

  \[em] um bitmask de [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).

- `cFunctions`

  \[em] o número de funções a serem recompiladas.

- `moduleIds`

  \[em] Especifica a parte `moduleId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.

- `methodIds`

  \[em] Especifica a parte `methodId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.

## <a name="remarks"></a>Comentários

O [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) não faz nenhum controle dos métodos embutidos. O criador de perfil era esperado para bloquear a inlinhação ou controlar o Intorno e chamar `RequestReJIT` para que todos os inlineers verifiquem se cada instância de um método embutido foi ReJITted. Isso representa um problema com o ReJIT na anexação, já que o criador de perfil não está presente para monitorar o inalinhamento. Esse método pode ser chamado para garantir que o conjunto completo de inlineers também será ReJITted.

## <a name="requirements"></a>Requisitos

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Confira também

- [Interface ICorProfilerInfo10](icorprofilerinfo10-interface.md)
