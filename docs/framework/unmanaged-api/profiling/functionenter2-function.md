---
title: Função FunctionEnter2
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177053"
---
# <a name="functionenter2-function"></a>Função FunctionEnter2
Notifica o profiler de que o controle está sendo passado para uma função e fornece informações sobre o quadro de pilha e argumentos de função. Esta função substitui a função [FunctionEnter.](functionenter-function.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>parâmetros

- `funcId`

  \[em] O identificador da função para a qual o controle é passado.

- `clientData`

  \[em] O identificador de função remapped, que o profiler anteriormente especificado usando a função [FunctionIDMapper.](functionidmapper-function.md)
  
- `func`

  \[em] `COR_PRF_FRAME_INFO` Um valor que aponta para informações sobre o quadro de pilha.
  
  O profiler deve tratá-lo como uma alça opaca que pode ser passada de volta para o mecanismo de execução no método [ICorProfilerInfo2::GetFunctionInfo2.](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- `argumentInfo`

  \[em] Um ponteiro para uma estrutura [de COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) que especifica os locais na memória dos argumentos da função.

  Para acessar as informações `COR_PRF_ENABLE_FUNCTION_ARGS` do argumento, a bandeira deve ser definida. O profiler pode usar o método [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir os sinalizadores de evento.

## <a name="remarks"></a>Comentários  
 Os valores `func` `argumentInfo` dos parâmetros e `FunctionEnter2` dos parâmetros não são válidos após o retorno da função porque os valores podem mudar ou ser destruídos.  
  
 A `FunctionEnter2` função é um retorno de chamada; você deve implementá-lo. A implementação `__declspec`deve`naked`usar o atributo () classe de armazenamento.  
  
 O motor de execução não salva nenhum registro antes de chamar esta função.  
  
- Na entrada, você deve salvar todos os registros que você usa, incluindo os da unidade de ponto flutuante (FPU).  
  
- Na saída, você deve restaurar a pilha, atirando todos os parâmetros que foram empurrados pelo seu interlocutor.  
  
 A implantação `FunctionEnter2` não deve bloquear porque vai atrasar a coleta de lixo. A implementação não deve tentar uma coleta de lixo porque a pilha pode não estar em um estado favorável à coleta de lixo. Se uma coleta de lixo for tentada, o tempo de execução será bloqueado até `FunctionEnter2` o retorno.  
  
 Além disso, a `FunctionEnter2` função não deve chamar para código gerenciado ou de qualquer forma causar uma alocação de memória gerenciada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função FunctionLeave2](functionleave2-function.md)
- [Função FunctionTailcall2](functiontailcall2-function.md)
- [Método SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
