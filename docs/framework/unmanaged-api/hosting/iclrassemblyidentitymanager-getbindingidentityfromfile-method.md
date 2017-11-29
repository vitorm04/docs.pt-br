---
title: "Método ICLRAssemblyIdentityManager::GetBindingIdentityFromFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 140240f5f108cdd26cd0e813d7fe47f102a3b941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a>Método ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
Obtém a identidade de assembly a associação de dados para o assembly no caminho de arquivo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzFilePath`  
 [in] O caminho para o arquivo a ser avaliada.  
  
 `dwFlags`  
 [in] Um valor de [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeração que indica o tipo de identidade de um assembly. Fornecido para extensibilidade futura. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor que suporta o common language runtime (CLR) versão 2.0.  
  
 `pwzBuffer`  
 [out] Um buffer que contém os dados de identidade de assembly opaco.  
  
 `pcchBufferSize`  
 [out no] Um ponteiro para o tamanho de `pwzBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método é retornado com êxito.|  
|E_INVALIDARG|Fornecido `pwzFilePath` é nulo.|  
|ERROR_INSUFFICIENT_BUFFER|O tamanho de `pwzBuffer` é muito pequeno.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `GetBindingIdentityFromFile`geralmente é chamado duas vezes. A primeira chamada fornece um valor nulo para `pwzBuffer`, e o método retorna o tamanho apropriado em `pcchBufferSize`. A segunda chamada fornece um buffer alocado adequadamente e o método retornará com os dados do buffer real após a conclusão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
