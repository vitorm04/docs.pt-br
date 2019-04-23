---
title: Método ICLRAppDomainResourceMonitor::GetCurrentSurvived
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408ef5419fbc2081d25ad442986ec8155bcb4c62
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141538"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>Método ICLRAppDomainResourceMonitor::GetCurrentSurvived
Obtém o número de bytes que sobreviveram o última completo, bloqueio de coleta de lixo e que são referenciados pelo domínio do aplicativo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwAppDomainId`  
 [in] A ID do domínio do aplicativo solicitado.  
  
 `pAppDomainBytesSurvived`  
 [out] Um ponteiro para o número de bytes que sobreviveram após a última coleta de lixo que são mantidos por esse domínio de aplicativo. Após uma coleta completa, esse número é preciso e completo. Após uma coleta efêmera, esse número é potencialmente incompleto. Esse parâmetro pode ser `null`.  
  
 `pRuntimeBytesSurvived`  
 [out] Um ponteiro para o número total de bytes que sobreviveram da última coleta de lixo. Após uma coleta completa, esse número representa o número de bytes que são mantidos em heaps gerenciados. Após uma coleta efêmera, esse número representa o número de bytes que são mantidos ativos em gerações efêmeras. Esse parâmetro pode ser `null`.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|COR_E_APPDOMAINUNLOADED|O domínio do aplicativo foi descarregado ou não existe.|  
  
## <a name="remarks"></a>Comentários  
 As estatísticas são atualizadas somente depois de completa, o bloqueio de coleta de lixo; ou seja, uma coleção que inclui todas as gerações e que interrompe o aplicativo durante a coleta ocorre. Por exemplo, o <xref:System.GC.Collect?displayProperty=nameWithType> sobrecarga do método executa uma completa de coleta de bloqueio. Coleta de lixo simultânea ocorre em segundo plano e não bloqueia o aplicativo.  
  
 O `GetCurrentSurvived` método é não gerenciado equivalente gerenciado <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> propriedade.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRAppDomainResourceMonitor](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Monitoramento de recursos de domínio do aplicativo](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
