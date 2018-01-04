---
title: "Função StackSnapshotCallback"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackSnapshotCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: StackSnapshotCallback
helpviewer_keywords: StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32cf21fb5a76fdec4daa322d53a8eb218ae2f2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="stacksnapshotcallback-function"></a>Função StackSnapshotCallback
Fornece o criador de perfil com informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante um exame da pilha, que é iniciado com a [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `funcId`  
 [in] Se esse valor for zero, esse retorno de chamada é para uma execução de quadros não gerenciados; Caso contrário, o identificador de uma função gerenciada e esse retorno de chamada é para um quadro gerenciado.  
  
 `ip`  
 [in] O valor do ponteiro de instrução do código nativo no quadro.  
  
 `frameInfo`  
 [in] Um `COR_PRF_FRAME_INFO` valor que faz referência a informações sobre o quadro de pilha. Esse valor é válido para uso somente durante esse retorno de chamada.  
  
 `contextSize`  
 [in] O tamanho do `CONTEXT` estrutura, que é referenciada pelo `context` parâmetro.  
  
 `context`  
 [in] Um ponteiro para um Win32 `CONTEXT` estrutura que representa o estado da CPU por este quadro.  
  
 O `context` parâmetro é válido somente se o sinalizador COR_PRF_SNAPSHOT_CONTEXT foi passado `ICorProfilerInfo2::DoStackSnapshot`.  
  
 `clientData`  
 [in] Um ponteiro para os dados do cliente, que são passados diretamente por meio da `ICorProfilerInfo2::DoStackSnapshot`.  
  
## <a name="remarks"></a>Comentários  
 O `StackSnapshotCallback` função é implementada pelo gerador de criador de perfil. Você deve limitar a complexidade do trabalho no `StackSnapshotCallback`. Por exemplo, ao usar `ICorProfilerInfo2::DoStackSnapshot` de maneira assíncrona, o thread de destino pode ser mantendo bloqueios. Se código dentro de `StackSnapshotCallback` requer os mesmos bloqueios, poderia causar um deadlock.  
  
 O `ICorProfilerInfo2::DoStackSnapshot` chamadas de método de `StackSnapshotCallback` função uma vez por quadro gerenciado ou de uma vez por execução de quadros não gerenciados. Se `StackSnapshotCallback` é chamado para uma execução de quadros não gerenciados, o criador de perfil pode usar o contexto de registro (referenciado pelo `context` parâmetro) para executar seu próprios não gerenciados na pilha. Nesse caso, o Win32 `CONTEXT` estrutura representa o estado da CPU para o quadro enviado mais recentemente dentro da execução de quadros não gerenciados. Embora o Win32 `CONTEXT` estrutura inclui valores para todos os registros, você deve depender apenas os valores do registro de ponteiro de pilha, registro de ponteiro de quadro, registro de ponteiro de instrução e não-volátil (que é, preservado) registra inteiro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
