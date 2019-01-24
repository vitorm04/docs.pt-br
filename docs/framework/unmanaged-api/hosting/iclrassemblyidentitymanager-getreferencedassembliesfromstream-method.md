---
title: Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35f7e168f143d9427bf6905e9b4c383d9a40cd1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514446"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a>Método ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
Obtém um ponteiro para um [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) objeto que contém os dados de identidade do assembly para os assemblies referenciados pelo assembly no fluxo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStream`  
 [in] Um ponteiro de interface para um `IStream` que contém o assembly a ser avaliada.  
  
 `dwFlags`  
 [in] Fornecido para extensibilidade futura. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que a versão atual do common language runtime (CLR) dá suporte.  
  
 `pExcludeAssembliesList`  
 [in] Um ponteiro para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objeto que contém dados de identidade de assembly para os assemblies a serem excluídos da `ppReferenceEnum`.  
  
 `ppReferenceEnum`  
 [out] Um ponteiro para o endereço de um `ICLRReferenceAssemblyEnum` objeto que contém os dados de identidade do assembly para os assemblies referenciados pelo assembly no `pStream`, exceto os assemblies no `pExcludeAssembliesList`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método é retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O chamador pode optar por excluir um conjunto de referências de assembly conhecidos na lista retornada. Este conjunto é definido pela `pExcludeAssembliesList`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interface ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
