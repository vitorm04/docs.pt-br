---
title: "Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 018dc40895a79788a9eef20082d764db0b2265c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy
Modifica a política de associação para o assembly especificado e cria uma nova versão da política.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzSourceAssemblyIdentity`  
 [in] A identidade do assembly para modificar.  
  
 `pwzTargetAssemblyIdentity`  
 [in] A nova identidade do assembly modificado.  
  
 `pbApplicationPolicy`  
 [in] Um ponteiro para um buffer que contém os dados de política de associação para o assembly modificar.  
  
 `cbAppPolicySize`  
 [in] O tamanho da política de associação a ser substituído.  
  
 `dwPolicyModifyFlags`  
 [in] Uma combinação de OR lógica de [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) valores, que indicam o controle de redirecionamento.  
  
 `pbNewApplicationPolicy`  
 [out] Um ponteiro para um buffer que contém os novos dados de política de associação.  
  
 `pcbNewAppPolicySize`  
 [out no] Um ponteiro para o tamanho do buffer de política de nova associação.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A política foi modificada com êxito.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`ou `pwzTargetAssemblyIdentity` era uma referência nula.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` é pequeno demais.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O `ModifyApplicationPolicy` método pode ser chamado duas vezes. A primeira chamada deve fornecer um valor nulo para o `pbNewApplicationPolicy` parâmetro. Essa chamada será retornada com o valor necessário para `pcbNewAppPolicySize`. A segunda chamada deve fornecer esse valor para `pcbNewAppPolicySize`e aponte para um buffer de tamanho para `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
