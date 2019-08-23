---
title: Método IGCHost::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 87ba947b9564f82f8daf8cd2ba0acac5cc3587ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928670"
---
# <a name="igchostsetgcstartuplimits-method"></a>Método IGCHost::SetGCStartupLimits
Define o tamanho do segmento e o tamanho máximo para a geração 0.  
  
> [!IMPORTANT]
> A partir do .NET Framework 4,5, você pode definir o tamanho do segmento e o tamanho máximo de geração 0 `DWORD` para valores maiores do que usar o método [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `SegmentSize`  
 no O tamanho do segmento usado pelo sistema de coleta de lixo.  
  
 `MaxGen0Size`  
 no O tamanho máximo para a geração 0.  
  
## <a name="remarks"></a>Comentários  
 O `SetGCStartupLimits` método pode ser chamado apenas uma vez. Esses valores não podem ser alterados posteriormente.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** GCHost.idl, GCHost.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
