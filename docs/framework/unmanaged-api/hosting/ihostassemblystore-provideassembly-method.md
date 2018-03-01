---
title: "Método IHostAssemblyStore::ProvideAssembly"
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
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2097c1ea64e5e9a2a09e0ec57243624b05eeea65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a>Método IHostAssemblyStore::ProvideAssembly
Obtém uma referência a um assembly que não é referenciado pelo [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que é retornado de [Ihostassemblymanager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). O common language runtime (CLR) chama `ProvideAssembly` para cada assembly que não aparecem na lista.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBindInfo`  
 [in] Um ponteiro para um [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instância que o host usa para determinar a certas características de ligação, incluindo a presença ou ausência de qualquer política de controle de versão e qual assembly para associar a.  
  
 `pAssemblyId`  
 [out] Um ponteiro para um identificador exclusivo para o assembly solicitado para este `IStream`.  
  
 `pHostContext`  
 [out] Um ponteiro para dados de host específico que são usados para determinar a evidência do assembly solicitado sem a necessidade de uma plataforma de chamada de invocação. `pHostContext`corresponde do <xref:System.Reflection.Assembly.HostContext%2A> propriedade gerenciada <xref:System.Reflection.Assembly> classe.  
  
 `ppStmAssemblyImage`  
 [out] Um ponteiro para o endereço de um `IStream` que contém a imagem de PE (executável portátil) a ser carregado, ou nulo se não foi possível encontrar o assembly.  
  
 `ppStmPDB`  
 [out] Um ponteiro para o endereço de um `IStream` que contém informações de depuração (PDB) do programa, ou nulo se o arquivo. PDB não pôde ser encontrado.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0X80070002)|O assembly solicitado não pôde ser localizado.|  
|E_NOT_SUFFICIENT_BUFFER|O tamanho do buffer especificado por `pAssemblyId` não é grande o suficiente para manter o identificador que o host deseja retornar.|  
  
## <a name="remarks"></a>Comentários  
 O valor de identidade é retornado para `pAssemblyId` é especificado pelo host. Identificadores devem ser exclusivos dentro do tempo de vida de um processo. O CLR usa esse valor como um identificador exclusivo para o fluxo. Ele verifica que cada valor em relação aos valores de `pAssemblyId` retornado por outras chamadas `ProvideAssembly`. Se o host retorna o mesmo `pAssemblyId` valor para outro `IStream`, o CLR verifica se o conteúdo de fluxo já foi mapeado. Nesse caso, o tempo de execução carrega a cópia existente da imagem em vez de mapeamento de um novo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
