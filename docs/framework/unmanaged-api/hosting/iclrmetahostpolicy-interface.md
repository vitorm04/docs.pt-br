---
title: Interface ICLRMetaHostPolicy
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9a70cf0812f84908630f109ef06aafa4b4f7525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434416"
---
# <a name="iclrmetahostpolicy-interface"></a>Interface ICLRMetaHostPolicy
Fornece o [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método, que retorna um ponteiro para uma interface comum de runtime (CLR) de idioma com base em critérios de uma política, gerenciados arquivo de assembly, versão e configuração.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|Fornece uma interface preferencial do CLR com base em critérios de uma política, gerenciados do arquivo de assembly, versão e a configuração.|  
  
## <a name="remarks"></a>Comentários  
 Você pode obter uma referência a esta interface chamando o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funcionar conforme mostrado no código a seguir:  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  Esta interface, na verdade, não carregar ou ativar o CLR, mas simplesmente retorna a versão do CLR preferencial com base nas versões disponíveis que estão instaladas ou carregadas.  
  
 O [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] API de hospedagem consolida políticas para que hosts com necessidades específicas podem usar a funcionalidade básica sem incorrer em penalidades não intencionais. Por exemplo, muitos as exportações mscoree associará a um CLR específico, embora um método não logicamente precisará-lo. O [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeração fornece diretivas de associação que são comuns para a maioria dos hosts.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
