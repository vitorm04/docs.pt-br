---
title: Método ICorConfiguration::AddDebuggerSpecialThread
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca33c8eb5e214cdaaa49905c311fd62042285d4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569278"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>Método ICorConfiguration::AddDebuggerSpecialThread
Para os serviços de depuração, indica que um thread específico deve ter permissão para continuar em execução enquanto o depurador tem um aplicativo interrompido durante cenários de depuração gerenciados ou não gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSpecialThreadId`  
 [in] A ID do thread que deve ter permissão para continuar a executar.  
  
## <a name="remarks"></a>Comentários  
 O thread especificado será permitido para executar código gerenciado ou inserir o tempo de execução de qualquer maneira. Um exemplo de tal thread seria um thread no processo para dar suporte a depuradores de script herdados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
