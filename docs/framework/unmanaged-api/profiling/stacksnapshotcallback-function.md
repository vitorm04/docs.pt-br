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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e71696282a3c9e6d25793b583ee19f306e167b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486232"
---
# <a name="stacksnapshotcallback-function"></a>Função StackSnapshotCallback
Fornece o criador de perfil com informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante uma movimentação de pilha, que é iniciada com o [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] Se esse valor for zero, esse retorno de chamada é para uma execução de quadros não gerenciados; Caso contrário, ele é o identificador de uma função gerenciada e esse retorno de chamada é para um quadro gerenciado.  
  
 `ip`  
 [in] O valor do ponteiro de instrução de código nativo no quadro.  
  
 `frameInfo`  
 [in] Um `COR_PRF_FRAME_INFO` valor que faz referência a informações sobre o quadro de pilha. Esse valor é válido para uso somente durante esse retorno de chamada.  
  
 `contextSize`  
 [in] O tamanho do `CONTEXT` estrutura, que é referenciada pelo `context` parâmetro.  
  
 `context`  
 [in] Um ponteiro para um Win32 `CONTEXT` estrutura que representa o estado da CPU para este quadro.  
  
 O `context` parâmetro é válido somente se o sinalizador COR_PRF_SNAPSHOT_CONTEXT foi passado `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Um ponteiro para os dados do cliente, que são passados diretamente por meio da `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Comentários  
 O `StackSnapshotCallback` função é implementada pelo gravador do criador de perfil. Você deve limitar a complexidade do trabalho feito em `StackSnapshotCallback`. Por exemplo, ao usar `ICorProfilerInfo2::DoStackSnapshot` de maneira assíncrona, o thread de destino pode manter bloqueios. Se código dentro do `StackSnapshotCallback` exige que os mesmos bloqueios, isso de poderia causar um deadlock.  
  
 O `ICorProfilerInfo2::DoStackSnapshot` chamadas de método a `StackSnapshotCallback` função uma vez por quadro gerenciado ou de uma vez por execução de quadros não gerenciados. Se `StackSnapshotCallback` é chamado de uma execução de quadros não gerenciados, o criador de perfil pode usar o contexto de registro (referenciado pelo `context` parâmetro) para executar seu próprio movimentação de pilha não gerenciada. Nesse caso, o Win32 `CONTEXT` estrutura representa o estado da CPU para o quadro mais recentemente enviadas por push dentro da execução de quadros não gerenciados. Embora o Win32 `CONTEXT` estrutura inclui valores para todos os registros, você deve contar somente os valores de registro de ponteiro de quadro, o registro de ponteiro de pilha, registro de ponteiro de instrução e não-volátil (que é, preservado) registros de inteiros.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Método DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
