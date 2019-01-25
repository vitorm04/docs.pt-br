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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45a7e0c793baa31d9efde2763570cd46a072fe86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546313"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>Método ICorProfilerInfo2::GetFunctionInfo2
Obtém a classe pai, o token de metadados e o `ClassID` de cada argumento de tipo, se presente, de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
#### <a name="parameters"></a>Parâmetros  
 `funcId`  
 [in] A ID da função para o qual obter o pai de classe e outras informações.  
  
 `frameInfo`  
 [in] Um `COR_PRF_FRAME_INFO` valor aponta para obter informações sobre um quadro de pilha.  
  
 `pClassId`  
 [out] Um ponteiro para a classe pai da função.  
  
 `pModuleId`  
 [out] Um ponteiro para o módulo no qual a classe pai da função é definido.  
  
 `pToken`  
 [out] Um ponteiro para o token de metadados para a função.  
  
 `cTypeArgs`  
 [in] O tamanho do `typeArgs` matriz.  
  
 `pcTypeArgs`  
 [out] Um ponteiro para o número total de `ClassID` valores.  
  
 `typeArgs`  
 [out] Uma matriz de `ClassID` valores, cada uma delas é a ID de um argumento de tipo da função. Quando o método retorna, `typeArgs` irá conter algumas ou todas as `ClassID` valores.  
  
## <a name="remarks"></a>Comentários  
 O código do criador de perfil pode chamar [ICorProfilerInfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) interface para um determinado módulo. O token de metadados que é retornado para o local referenciado pelo `pToken` , em seguida, pode ser usado para acessar os metadados para a função.  
  
 Os argumentos de ID e o tipo de classe que são retornados por meio de `pClassId` e `typeArgs` parâmetros dependem do valor que é passado a `frameInfo` parâmetro, conforme mostrado na tabela a seguir.  
  
|Valor da `frameInfo` parâmetro|Resultado|  
|----------------------------------------|------------|  
|Um `COR_PRF_FRAME_INFO` valor que foi obtido um `FunctionEnter2` retorno de chamada|O `ClassID`, retornada no local referenciado pela `pClassId`, e todos os tipo de argumentos, retornados no `typeArgs` de matriz, será exata.|  
|Um `COR_PRF_FRAME_INFO` que foi obtido de uma fonte diferente de um `FunctionEnter2` retorno de chamada|Exato `ClassID` e argumentos de tipo não podem ser determinados. Ou seja, o `ClassID` podem ser nulos e alguns argumentos de tipo podem vir como <xref:System.Object>.|  
|Zero|Exato `ClassID` e argumentos de tipo não podem ser determinados. Ou seja, o `ClassID` podem ser nulos e alguns argumentos de tipo podem vir como <xref:System.Object>.|  
  
 Após `GetFunctionInfo2` é retornado, você deve verificar se o `typeArgs` buffer era grande o suficiente para conter todos os `ClassID` valores. Para fazer isso, o valor de comparação que `pcTypeArgs` aponta para com o valor da `cTypeArgs` parâmetro. Se `pcTypeArgs` aponta para um valor maior que `cTypeArgs` dividida pelo tamanho de uma `ClassID` o valor, alocar uma maior `pcTypeArgs` do buffer, atualize `cTypeArgs` com o novo e maior tamanho e a chamada `GetFunctionInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetFunctionInfo2` com um comprimento de zero `pcTypeArgs` buffer para obter o tamanho do buffer correto. Em seguida, você pode definir o tamanho do buffer para o valor retornado na `pcTypeArgs` dividida pelo tamanho de um `ClassID` valor e chame `GetFunctionInfo2` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
