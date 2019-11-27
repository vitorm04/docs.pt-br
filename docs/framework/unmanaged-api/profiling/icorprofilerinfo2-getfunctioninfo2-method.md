---
title: Método ICorProfilerInfo2::GetFunctionInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
ms.openlocfilehash: 11f9a186f5ec5e3b9e718a3ccd43b35b66d28078
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433185"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>Método ICorProfilerInfo2::GetFunctionInfo2
Obtém a classe pai, o token de metadados e a `ClassID` de cada argumento de tipo, se presente, de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `funcId`  
 no A ID da função para a qual obter a classe pai e outras informações.  
  
 `frameInfo`  
 no Um valor `COR_PRF_FRAME_INFO` que aponta para informações sobre um registro de ativação.  
  
 `pClassId`  
 fora Um ponteiro para a classe pai da função.  
  
 `pModuleId`  
 fora Um ponteiro para o módulo no qual a classe pai da função é definida.  
  
 `pToken`  
 fora Um ponteiro para o token de metadados para a função.  
  
 `cTypeArgs`  
 no O tamanho da matriz de `typeArgs`.  
  
 `pcTypeArgs`  
 fora Um ponteiro para o número total de `ClassID` valores.  
  
 `typeArgs`  
 fora Uma matriz de valores `ClassID`, cada qual é a ID de um argumento de tipo da função. Quando o método retornar, `typeArgs` conterá alguns ou todos os valores de `ClassID`.  
  
## <a name="remarks"></a>Comentários  
 O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) para um determinado módulo. O token de metadados que é retornado para o local referenciado por `pToken` pode ser usado para acessar os metadados para a função.  
  
 Os argumentos ID de classe e tipo retornados por meio dos parâmetros `pClassId` e `typeArgs` dependem do valor que é passado no parâmetro `frameInfo`, conforme mostrado na tabela a seguir.  
  
|Valor do parâmetro `frameInfo`|Resultado|  
|----------------------------------------|------------|  
|Um valor `COR_PRF_FRAME_INFO` que foi obtido de um retorno de chamada `FunctionEnter2`|O `ClassID`, retornado no local referenciado por `pClassId`e todos os argumentos de tipo, retornados na matriz de `typeArgs`, será exato.|  
|Um `COR_PRF_FRAME_INFO` que foi obtido de uma fonte diferente de um retorno de chamada `FunctionEnter2`|Os argumentos exatos `ClassID` e de tipo não podem ser determinados. Ou seja, o `ClassID` pode ser nulo e alguns argumentos de tipo podem voltar como <xref:System.Object>.|  
|Zero|Os argumentos exatos `ClassID` e de tipo não podem ser determinados. Ou seja, o `ClassID` pode ser nulo e alguns argumentos de tipo podem voltar como <xref:System.Object>.|  
  
 Depois que `GetFunctionInfo2` retorna, você deve verificar se o buffer de `typeArgs` era grande o suficiente para conter todos os valores de `ClassID`. Para fazer isso, compare o valor que `pcTypeArgs` aponta com o valor do parâmetro `cTypeArgs`. Se `pcTypeArgs` apontar para um valor maior que `cTypeArgs` dividido pelo tamanho de um valor de `ClassID`, aloque um buffer de `pcTypeArgs` maior, atualize `cTypeArgs` com o tamanho novo, maior e chame `GetFunctionInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetFunctionInfo2` com um buffer de `pcTypeArgs` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado em `pcTypeArgs` dividido pelo tamanho de um valor de `ClassID` e chamar `GetFunctionInfo2` novamente.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
