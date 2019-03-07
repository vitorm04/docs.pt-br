---
title: Método ICorRuntimeHost::SwitchInLogicalThreadState
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d12555fb53a6c1b21f161402da77860adcf0a4b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478902"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a>Método ICorRuntimeHost::SwitchInLogicalThreadState
Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFiberCookie`  
 [in] Cookie que indica a fibra para usar.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versão do .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
