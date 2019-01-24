---
title: Método ICLRMetaHost::ExitProcess
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbf3c00eafe47556c6b46e1acb687a19df5a2b28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601747"
---
# <a name="iclrmetahostexitprocess-method"></a>Método ICLRMetaHost::ExitProcess
Tenta desligar normalmente o carregados todos os tempos de execução e, em seguida, encerra o processo. Substitui o [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `iExitCode`  
 [in] O código de saída para o processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método nunca retorna, portanto, seu valor de retorno será indefinido.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
