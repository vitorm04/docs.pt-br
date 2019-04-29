---
title: Enumeração CorDebugCodeInvokeKind
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3b4906f988d09f7b01aee40e8f63b589da5f33d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609198"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Enumeração CorDebugCodeInvokeKind
Descreve como uma função exportada invocará o código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|Se algum código gerenciado for invocado por este método, precisará ser localizadas por eventos explícitos ou pontos de interrupção posteriormente.<br /><br /> --ou--<br /><br /> Podemos perder parte do código gerenciado que este método chama porque não há nenhuma maneira fácil de pará-lo.<br /><br /> --ou--<br /><br /> O método nunca pode invocar um código gerenciado.|  
|`CODE_INVOKE_KIND_RETURN`|Esse método invocará o código gerenciado por meio de uma instrução de retorno. Sair deve dar no próximo código gerenciado.|  
|`CODE_INVOKE_KIND_TAILCALL`|Esse método invocará o código gerenciado por meio de chamada tail. Seguir uma etapa única e ignorar quaisquer instruções de chamada devem dar no código gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 Essa enumeração é usada pelo [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) método para fornecer informações sobre como percorrer o código gerenciado.  
  
> [!NOTE]
>  Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
