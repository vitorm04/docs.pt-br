---
title: Interface ICorDebugProcess2
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 1ef6af11851acbe0f7e9469c9432ff09f9228608
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792502"
---
# <a name="icordebugprocess2-interface"></a>Interface ICorDebugProcess2
Uma extensão lógica da interface ICorDebugProcess, que representa um processo que executa código gerenciado.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md)|Remove um ponto de interrupção no deslocamento especificado que foi definido por uma chamada anterior para `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[Método GetDesiredNGENCompilerFlags](icordebugprocess2-getdesiredngencompilerflags-method.md)|Obtém os sinalizadores que devem ser definidos para o Common Language Runtime (CLR) para carregar a imagem no processo referenciado por este `ICorDebugProcess2`.|  
|[Método GetReferenceValueFromGCHandle](icordebugprocess2-getreferencevaluefromgchandle-method.md)|Obtém um ponteiro de referência para o objeto gerenciado especificado que tem um identificador de coleta de lixo.|  
|[Método GetThreadForTaskID](icordebugprocess2-getthreadfortaskid-method.md)|Obtém o thread no qual a tarefa com o identificador especificado está em execução.|  
|[Método GetVersion](icordebugprocess2-getversion-method.md)|Obtém a versão do CLR no qual o processo que está sendo depurado está em execução.|  
|[Método SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md)|Define os sinalizadores que são necessários para o compilador JIT (just-in-time) carregar uma imagem no processo que está sendo depurado.|  
|[Método SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)|Define um ponto de interrupção não gerenciado no deslocamento da imagem nativa especificada.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
