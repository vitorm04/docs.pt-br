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
ms.openlocfilehash: e0493ed3f8796019d5715ef468c88675b9970a39
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973836"
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
  
#### <a name="parameters"></a>Parâmetros  
 `pNativeCodeStartAddress`  
 no Um ponteiro para o início de uma função nativa.  

 `cCodeInfos`  
 no O tamanho da `codeInfos` matriz.  
  
 `pcCodeInfos`  
 fora Um ponteiro para o número total de estruturas [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) disponíveis.  
  
 `codeInfos`  
 fora Um buffer fornecido pelo chamador. Depois que o método retorna, ele contém uma matriz `COR_PRF_CODE_INFO` de estruturas, cada uma delas descreve um bloco de código nativo.  
  
## <a name="remarks"></a>Comentários  
 O `GetCodeInfo4` método é semelhante a [GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md), exceto pelo fato de que ele pode pesquisar informações de código para versões nativas diferentes de um método.  
  
> [!NOTE]
>  `GetCodeInfo4`pode disparar uma coleta de lixo.
  
 As extensões são classificadas em ordem crescente de deslocamento de Common Intermediate Language (CIL).  
  
 Depois `GetCodeInfo4` de retornar, você deve verificar se `codeInfos` o buffer foi grande o suficiente para conter todas as estruturas [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . Para fazer isso, compare o valor de `cCodeInfos` com o valor `cchName` do parâmetro. Se `cCodeInfos` dividido pelo tamanho de uma estrutura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) for menor que `pcCodeInfos`, aloque um buffer maior `codeInfos` , atualize `cCodeInfos` com o novo tamanho, maior e chame `GetCodeInfo4` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetCodeInfo4` com um buffer de comprimento `codeInfos` zero para obter o tamanho de buffer correto. Em seguida, você pode `codeInfos` definir o tamanho do buffer para o `pcCodeInfos`valor retornado em, multiplicado pelo tamanho de uma estrutura [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) e `GetCodeInfo4` chamar novamente.   
  

## <a name="requirements"></a>Requisitos  
 **Compatíveis** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)

