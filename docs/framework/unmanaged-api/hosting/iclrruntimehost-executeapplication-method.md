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
ms.openlocfilehash: 56a49b3d08b58da109924267e6c23c188efefe29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436066"
---
# <a name="iclrruntimehostexecuteapplication-method"></a>Método ICLRRuntimeHost::ExecuteApplication
Usado em cenários de implantação de ClickOnce baseado no manifesto para especificar o aplicativo a ser ativado em um novo domínio. Para obter mais informações sobre esses cenários, consulte [segurança ClickOnce e implantação](/visualstudio/deployment/clickonce-security-and-deployment).  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pwzAppFullName`  
 [in] O nome completo do aplicativo, conforme definido para <xref:System.ApplicationIdentity>.  
  
 `dwManifestPaths`  
 [in] O número de cadeias de caracteres dentro de `ppwzManifestPaths` matriz.  
  
 `ppwzManifestPaths`  
 [in] Opcional. Uma matriz de cadeia de caracteres que contém os caminhos do manifesto do aplicativo.  
  
 `dwActivationData`  
 [in] O número de cadeias de caracteres dentro de `ppwzActivationData` matriz.  
  
 `ppwzActivationData`  
 [in] Opcional. Uma matriz de cadeia de caracteres que contém os dados de ativação do aplicativo, como a parte da cadeia de caracteres de consulta da URL para os aplicativos implantados pela Web.  
  
 `pReturnValue`  
 [out] O valor retornado do ponto de entrada do aplicativo.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ExecuteApplication` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `ExecuteApplication` é usada para ativar aplicativos ClickOnce em um domínio de aplicativo recém-criado.  
  
 O `pReturnValue` parâmetro de saída é definido como o valor retornado pelo aplicativo. Se você fornecer um valor nulo para `pReturnValue`, `ExecuteApplication` não falha, mas não retorna um valor.  
  
> [!IMPORTANT]
>  Não chame o [método Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método antes de chamar o `ExecuteApplication` método para ativar um aplicativo baseado no manifesto. Se o `Start` método é chamado pela primeira vez, o `ExecuteApplication` haverá falha na chamada de método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [Método SetAppDomainManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [Passo a passo: baixando assemblies sob demanda com a API de implantação do ClickOnce usando o designer](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
