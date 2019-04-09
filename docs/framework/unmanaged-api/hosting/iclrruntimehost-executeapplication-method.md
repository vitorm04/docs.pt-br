---
title: Método ICLRRuntimeHost::ExecuteApplication
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ce7e9ff4041abd1e89330bd3a565b755875d3b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194221"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>Método ICLRRuntimeHost::ExecuteApplication
Usado em cenários de implantação de ClickOnce baseado em manifesto para especificar o aplicativo a ser ativado em um novo domínio. Para obter mais informações sobre esses cenários, consulte [implantação e segurança do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwzAppFullName`  
 [in] O nome completo do aplicativo, conforme definido para <xref:System.ApplicationIdentity>.  
  
 `dwManifestPaths`  
 [in] O número de cadeias de caracteres contidos no `ppwzManifestPaths` matriz.  
  
 `ppwzManifestPaths`  
 [in] Opcional. Uma matriz de cadeia de caracteres que contém os caminhos do manifesto do aplicativo.  
  
 `dwActivationData`  
 [in] O número de cadeias de caracteres contidos no `ppwzActivationData` matriz.  
  
 `ppwzActivationData`  
 [in] Opcional. Uma matriz de cadeia de caracteres que contém dados de ativação do aplicativo, como a parte da cadeia de caracteres de consulta da URL para aplicativos implantados pela Web.  
  
 `pReturnValue`  
 [out] O valor retornado do ponto de entrada do aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `ExecuteApplication` é usada para ativar aplicativos ClickOnce em um domínio de aplicativo recém-criado.  
  
 O `pReturnValue` parâmetro de saída é definido como o valor retornado pelo aplicativo. Se você fornecer um valor null para `pReturnValue`, `ExecuteApplication` não falhar, mas não retorna um valor.  
  
> [!IMPORTANT]
>  Não chame o [método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método antes de chamar o `ExecuteApplication` método para ativar um aplicativo baseado em manifesto. Se o `Start` método é chamado pela primeira vez, o `ExecuteApplication` chamada de método falhará.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Método SetAppDomainManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [Passo a passo: Baixando Assemblies sob demanda com a implantação do ClickOnce usando o Designer de API](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
