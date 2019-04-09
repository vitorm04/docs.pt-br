---
title: Método IHostAssemblyStore::ProvideAssembly
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a8be1e330338043df50bd80576b5aa65447b9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111898"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>Método IHostAssemblyStore::ProvideAssembly
Obtém uma referência a um assembly que não é referenciado pela [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que é retornado de [ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). O common language runtime (CLR) chama `ProvideAssembly` para cada assembly que não aparece na lista.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `pBindInfo`  
 [in] Um ponteiro para um [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instância que o host usa para determinar a certas características de associação, inclusive a presença ou ausência de qualquer política de controle de versão e qual assembly para associar a.  
  
 `pAssemblyId`  
 [out] Um ponteiro para um identificador exclusivo para o assembly solicitado para este `IStream`.  
  
 `pHostContext`  
 [out] Um ponteiro para dados específicos do host que são usados para determinar a evidência do assembly solicitado sem a necessidade de uma plataforma de chamada de invocação. `pHostContext` corresponde do <xref:System.Reflection.Assembly.HostContext%2A> propriedade de gerenciado <xref:System.Reflection.Assembly> classe.  
  
 `ppStmAssemblyImage`  
 [out] Um ponteiro para o endereço de um `IStream` que contém a imagem PE (executável portátil) para ser carregado, ou nulo se não foi possível encontrar o assembly.  
  
 `ppStmPDB`  
 [out] Um ponteiro para o endereço de um `IStream` que contém as informações de depuração (PDB) do programa, ou nulo se não foi possível encontrar o arquivo. PDB.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Não foi possível localizar o assembly solicitado.|  
|E_NOT_SUFFICIENT_BUFFER|O tamanho do buffer especificado por `pAssemblyId` não é grande o suficiente para manter o identificador que o host quiser retornar.|  
  
## <a name="remarks"></a>Comentários  
 O valor de identidade é retornado para `pAssemblyId` é especificado pelo host. Identificadores devem ser exclusivos dentro do tempo de vida de um processo. O CLR usa esse valor como um identificador exclusivo para o fluxo. Ele verifica que cada valor em relação os valores para `pAssemblyId` retornado por outras chamadas para `ProvideAssembly`. Se o host retorna o mesmo `pAssemblyId` valor para outro `IStream`, o CLR verifica se o conteúdo de fluxo já foi mapeado. Nesse caso, o tempo de execução carrega a cópia existente da imagem em vez de mapeamento de um novo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
