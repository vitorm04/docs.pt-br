---
title: Função StackSnapshotCallback
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427070"
---
# <a name="stacksnapshotcallback-function"></a>Função StackSnapshotCallback
Fornece ao criador de perfil informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante uma movimentação de pilha, que é iniciada pelo método [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `funcId`  
 no Se esse valor for zero, esse retorno de chamada será para uma execução de quadros não gerenciados; caso contrário, é o identificador de uma função gerenciada e esse retorno de chamada é para um quadro gerenciado.  
  
 `ip`  
 no O valor do ponteiro de instrução de código nativo no quadro.  
  
 `frameInfo`  
 no Um valor `COR_PRF_FRAME_INFO` que faz referência a informações sobre o registro de ativação. Esse valor é válido para uso somente durante este retorno de chamada.  
  
 `contextSize`  
 no O tamanho da estrutura de `CONTEXT`, que é referenciada pelo parâmetro `context`.  
  
 `context`  
 no Um ponteiro para uma estrutura de `CONTEXT` Win32 que representa o estado da CPU para esse quadro.  
  
 O parâmetro `context` será válido somente se o sinalizador de COR_PRF_SNAPSHOT_CONTEXT foi passado em `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 no Um ponteiro para os dados do cliente, que é passado diretamente por meio de `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Comentários  
 A função `StackSnapshotCallback` é implementada pelo gravador do criador de perfil. Você deve limitar a complexidade do trabalho feito em `StackSnapshotCallback`. Por exemplo, ao usar `ICorProfilerInfo2::DoStackSnapshot` de maneira assíncrona, o thread de destino pode estar mantendo bloqueios. Se o código dentro de `StackSnapshotCallback` exigir os mesmos bloqueios, um deadlock poderá acontecer.  
  
 O método `ICorProfilerInfo2::DoStackSnapshot` chama a função `StackSnapshotCallback` uma vez por quadro gerenciado ou uma vez por execução de quadros não gerenciados. Se `StackSnapshotCallback` for chamado para uma execução de quadros não gerenciados, o criador de perfil poderá usar o contexto de registro (referenciado pelo parâmetro `context`) para executar sua própria movimentação de pilha não gerenciada. Nesse caso, a estrutura de `CONTEXT` do Win32 representa o estado da CPU para o quadro enviado mais recentemente dentro da execução de quadros não gerenciados. Embora a estrutura de `CONTEXT` do Win32 inclua valores para todos os registros, você deve confiar apenas nos valores do registro de ponteiro de pilha, registro de ponteiro de quadro, registro de ponteiro de instrução e os registros de inteiros não voláteis (ou seja, preservados).  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
