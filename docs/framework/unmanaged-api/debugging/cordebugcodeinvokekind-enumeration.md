---
title: "Enumeração CorDebugCodeInvokeKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCodeInvokeKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d46a47c7c655a960224bb836be0ea37cd07c8038
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugcodeinvokekind-enumeration"></a>Enumeração CorDebugCodeInvokeKind
Descreve como uma função exportada invoca código gerenciado.  
  
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
 Essa enumeração é usada pelo [Icordebugprocess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) método para fornecer informações sobre percorrendo o código gerenciado.  
  
> [!NOTE]
>  Essa enumeração é destinada ao uso no .NET Native somente para cenários de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
