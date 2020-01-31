---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3e3e3afc221d153ff3573126ff10014d39af761a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868298"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>Método ICorProfilerInfo9:: GetCodeInfo4

Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>Parâmetros

- `pNativeCodeStartAddress`

  \[em] um ponteiro para o início de uma função nativa.

- `cCodeInfos`

  \[em] o tamanho da matriz de `codeInfos`.

- `pcCodeInfos`

  \[out] um ponteiro para o número total de estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) disponíveis.

- `codeInfos`

  \[out] um buffer fornecido pelo chamador. Depois que o método retorna, ele contém uma matriz de estruturas `COR_PRF_CODE_INFO`, cada uma delas descreve um bloco de código nativo.

## <a name="remarks"></a>Comentários

O método `GetCodeInfo4` é semelhante a [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), exceto pelo fato de que ele pode pesquisar informações de código para versões nativas diferentes de um método.

> [!NOTE]
> `GetCodeInfo4` pode disparar uma coleta de lixo.

As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).

Depois que `GetCodeInfo4` retorna, você deve verificar se o buffer de `codeInfos` era grande o suficiente para conter todas as estruturas de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . Para fazer isso, compare o valor de `cCodeInfos` com o valor do parâmetro `cchName`. Se `cCodeInfos` dividido pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) for menor do que `pcCodeInfos`, aloque um buffer de `codeInfos` maior, atualize `cCodeInfos` com o tamanho novo, maior e chame `GetCodeInfo4` novamente.

Como alternativa, você pode primeiro chamar `GetCodeInfo4` com um buffer de `codeInfos` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer de `codeInfos` para o valor retornado em `pcCodeInfos`, multiplicado pelo tamanho de uma estrutura de [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) e chamar `GetCodeInfo4` novamente.

## <a name="requirements"></a>Requisitos do

**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Cabeçalho:** CorProf. idl, CorProf. h

**Biblioteca:** CorGuids.lib

**Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo9](ICorProfilerInfo9-interface.md)
