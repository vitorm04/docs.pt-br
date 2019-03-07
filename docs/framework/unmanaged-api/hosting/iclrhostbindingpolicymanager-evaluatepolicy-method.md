---
title: Método ICLRHostBindingPolicyManager::EvaluatePolicy
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3310f584475a4d6a6f0e3e790db13875faf60cf2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466681"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>Método ICLRHostBindingPolicyManager::EvaluatePolicy
Avalia a política de associação em nome do host.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwzReferenceIdentity`  
 [in] Uma referência ao assembly antes da avaliação da política.  
  
 `pbApplicationPolicy`  
 [in] Um ponteiro para um buffer que contém os dados de política.  
  
 `cbAppPolicySize`  
 [in] O tamanho do `pbApplicationPolicy` buffer.  
  
 `pwzPostPolicyReferenceIdentity`  
 [out] Uma referência ao assembly após a avaliação dos novos dados de política.  
  
 `pcchPostPolicyReferenceIdentity`  
 [no, out] Um ponteiro para o tamanho do buffer de referência de identidade de assembly após a avaliação dos novos dados de política.  
  
 `pdwPoliciesApplied`  
 [out] Um ponteiro para uma combinação OR lógico de [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) valores, que indica quais diretivas foram aplicadas.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A avaliação foi concluída com êxito.|  
|E_INVALIDARG|Tanto `pwzReferenceIdentity` ou `pbApplicationPolicy` é uma referência nula.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize` é pequeno demais.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Depois que um método retorna E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O `EvaluatePolicy` método permite que o host para influenciar a política de associação de assembly específico de host de manter os requisitos de controle de versão. O mecanismo de políticas em si permanece dentro do CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
