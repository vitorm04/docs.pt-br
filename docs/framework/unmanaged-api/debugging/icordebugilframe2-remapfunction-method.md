---
title: Método ICorDebugILFrame2::RemapFunction
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdcc2eccbb24a92643415db8e5d267033ac1ca0a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758756"
---
# <a name="icordebugilframe2remapfunction-method"></a>Método ICorDebugILFrame2::RemapFunction
Remapeia uma função editada, especificando o novo deslocamento do Microsoft intermediate language (MSIL)  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newILOffset`  
 [in] Novo deslocamento da MSIL do quadro de pilhas no qual o ponteiro de instrução deve ser colocado. Esse valor deve ser um ponto de sequência.  
  
 É responsabilidade do chamador para garantir a validade desse valor. Por exemplo, o deslocamento do MSIL não é válido se ele está fora dos limites da função.  
  
## <a name="remarks"></a>Comentários  
 Quando a função de um quadro foi editada, o depurador pode chamar o `RemapFunction` método trocar a versão mais recente da função do quadro para que ele pode ser executado. A execução do código será iniciada no deslocamento especificado do MSIL.  
  
> [!NOTE]
>  Chamando `RemapFunction`, como chamar [icordebugilframe:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), imediatamente invalidará todas as interfaces de depuração que estão relacionadas à geração de um rastreamento de pilha do thread. Essas interfaces incluem [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame e ICorDebugNativeFrame.  
  
 O `RemapFunction` método pode ser chamado somente no contexto do quadro atual e somente em um dos seguintes casos:  
  
- Após o recebimento de uma [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) retorno de chamada que ainda não foi continuado.  
  
- Embora a execução do código é interrompida devido uma [icordebugmanagedcallback:: Editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) eventos para este quadro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
