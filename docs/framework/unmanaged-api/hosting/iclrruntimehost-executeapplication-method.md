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
ms.openlocfilehash: 38938de335e5f0d7cb8051554c400f16df012362
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965350"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>Método ICLRRuntimeHost::ExecuteApplication
Usado em cenários de implantação ClickOnce baseados em manifesto para especificar o aplicativo a ser ativado em um novo domínio. Para obter mais informações sobre esses cenários, consulte [segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no O nome completo do aplicativo, conforme definido para <xref:System.ApplicationIdentity>.  
  
 `dwManifestPaths`  
 no O número de cadeias de caracteres `ppwzManifestPaths` contidas na matriz.  
  
 `ppwzManifestPaths`  
 [in] Opcional. Uma matriz de cadeia de caracteres que contém caminhos de manifesto para o aplicativo.  
  
 `dwActivationData`  
 no O número de cadeias de caracteres `ppwzActivationData` contidas na matriz.  
  
 `ppwzActivationData`  
 [in] Opcional. Uma matriz de cadeia de caracteres que contém os dados de ativação do aplicativo, como a parte da cadeia de caracteres de consulta da URL para aplicativos implantados na Web.  
  
 `pReturnValue`  
 fora O valor retornado do ponto de entrada do aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `ExecuteApplication`é usado para ativar aplicativos ClickOnce em um domínio de aplicativo recém-criado.  
  
 O `pReturnValue` parâmetro de saída é definido como o valor retornado pelo aplicativo. Se você fornecer um valor de NULL para `pReturnValue`, `ExecuteApplication` o não falhará, mas não retornará um valor.  
  
> [!IMPORTANT]
> Não chame o método [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) antes de chamar o `ExecuteApplication` método para ativar um aplicativo baseado em manifesto. Se o `Start` método for chamado primeiro, a `ExecuteApplication` chamada do método falhará.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Método SetAppDomainManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [Passo a passo: Como baixar assemblies sob demanda com a API de implantação do ClickOnce usando o designer](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
