---
title: Estrutura StackTrace_SimpleContext
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210419"
---
# <a name="stacktracesimplecontext-structure"></a>Estrutura StackTrace_SimpleContext
Fornece um contexto simples que pode ser usado em lugar de uma estrutura `CONTEXT` completa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`StackOffset`|O ponteiro de pilha, ou o ponteiro de pilha de enter (ESP) em x86 plataformas.|  
|`FrameOffset`|O deslocamento do quadro, ou o registro de EBP no x86 plataformas.|  
|`InstructionOffset`|O ponteiro de instrução ou o ponteiro de instrução de enter (EIP) em x86 plataformas.|  
  
## <a name="remarks"></a>Comentários  
 Como as funções de rastreamento de pilha normalmente precisam retornar apenas o endereço, deslocamento do quadro e endereço de pilha, opcionalmente, você pode usar o `SimpleContext` estrutura em vez de um grande `CONTEXT` estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** SOS_Stacktrace.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
