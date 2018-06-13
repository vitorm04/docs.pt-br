---
title: Método ICorDebugProcess5::EnableNGENPolicy
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c598491acd27223a8a41234ddf2c6b8e6f005d52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423137"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>Método ICorDebugProcess5::EnableNGENPolicy
Define um valor que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ePolicy`  
 [in] Um [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) constante que determina como um aplicativo carrega imagens nativas durante a execução em um depurador gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se a política está definida com êxito, o método retornará `S_OK`. Se `ePolicy` está fora do intervalo dos valores enumerados definidos por [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), o método retorna `E_INVALIDARG` e a chamada do método não tem nenhum efeito. Se a política de gerador de imagem nativa (Ngen.exe) não pode ser atualizada, o método retornará `E_FAIL`.  
  
 O `ICorDebugProcess5::EnableNGenPolicy` método pode ser chamado a qualquer momento durante o tempo de vida do processo. A política está em vigor para todos os módulos que estão carregados depois que a política está definida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
