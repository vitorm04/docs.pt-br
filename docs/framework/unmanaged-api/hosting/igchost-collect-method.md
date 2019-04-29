---
title: Método IGCHost::Collect
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacb454783cfb8f90ea5a73807f0a199e16475d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927832"
---
# <a name="igchostcollect-method"></a>Método IGCHost::Collect
Força uma coleta ocorrer para a geração de determinado, independentemente do estado da coleta de lixo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `Generation`  
 [in] A geração na qual executar a coleta de lixo. Um valor de -1 indica que todas as gerações passará por uma coleta de lixo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl, GCHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
