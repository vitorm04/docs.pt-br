---
title: Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy
ms.date: 03/30/2017
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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178095"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>Método ICLRHostBindingPolicyManager::ModifyApplicationPolicy
Modifica a política vinculativa para a montagem especificada e cria uma nova versão da política.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>parâmetros  
 `pwzSourceAssemblyIdentity`  
 [em] A identidade da assembléia para modificar.  
  
 `pwzTargetAssemblyIdentity`  
 [em] A nova identidade da montagem modificada.  
  
 `pbApplicationPolicy`  
 [em] Um ponteiro para um buffer que contém os dados de diretiva de vinculação para a montagem modificar.  
  
 `cbAppPolicySize`  
 [em] O tamanho da política de vinculação a ser substituída.  
  
 `dwPolicyModifyFlags`  
 [em] Uma combinação ou lógica de valores [EHostBindingPolicyModifyModifyFlags,](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) indicando o controle do redirecionamento.  
  
 `pbNewApplicationPolicy`  
 [fora] Um ponteiro para um buffer que contém os novos dados de diretiva de vinculação.  
  
 `pcbNewAppPolicySize`  
 [dentro, fora] Um ponteiro para o tamanho do novo buffer de diretiva de vinculação.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A política foi modificada com sucesso.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`ou `pwzTargetAssemblyIdentity` era uma referência nula.|  
|Error_insufficient_buffer|`pbNewApplicationPolicy` é pequeno demais.|  
|Host_e_clrnotavailable|O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.|  
|HOST_E_TIMEOUT|A chamada acabou.|  
|HOST_E_NOT_OWNER|O interlocutor não é dono da fechadura.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.|  
|E_FAIL|Uma falha catastrófica desconhecida ocorreu. Depois que um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo. Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O `ModifyApplicationPolicy` método pode ser chamado duas vezes. A primeira chamada deve fornecer `pbNewApplicationPolicy` um valor nulo para o parâmetro. Esta chamada retornará com `pcbNewAppPolicySize`o valor necessário para . A segunda chamada deve `pcbNewAppPolicySize`fornecer esse valor para , `pbNewApplicationPolicy`e apontar para um buffer desse tamanho para .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
