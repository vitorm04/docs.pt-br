---
title: Método IHostAssemblyStore::ProvideModule
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb0e3bcb563387c5ee7f95d2aa6f6b5ec771f3a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717526"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>Método IHostAssemblyStore::ProvideModule
Resolve um arquivo de recurso de módulo dentro de um assembly ou um vinculados (mas não inserida).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBindInfo`  
 [in] Um ponteiro para um [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instância que descreve o módulo solicitado <xref:System.AppDomain>, assembly e o nome do módulo.  
  
 `pdwModuleId`  
 [out] Um ponteiro para um identificador exclusivo para o `IStream` que contém o módulo carregado.  
  
 `ppStmModuleImage`  
 [out] Um ponteiro para o endereço de um `IStream` do objeto, que contém a imagem PE (executável portátil) a ser carregado, ou nulo se o módulo não pôde ser encontrado.  
  
 `ppStmPDB`  
 [out] Um ponteiro para o endereço de um `IStream` de objeto, que contém as informações de depuração (PDB) do programa para o módulo solicitada ou null se não foi possível encontrar o arquivo. PDB.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ProvideModule` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|O assembly solicitado ou recurso vinculado não foi localizado.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` não é grande o suficiente para conter o identificador que o host deseja retornar.|  
  
## <a name="remarks"></a>Comentários  
 O valor de identidade é retornado para `pdwModuleId` é especificado pelo host. Identificadores devem ser exclusivos dentro do tempo de vida de um processo. O CLR usa esse valor como o identificador exclusivo para o fluxo associado. Ele verifica que cada valor em relação os valores para `pAssemblyId` retornados por chamadas para [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) contra os valores para `pdwModuleId` retornado por outras chamadas para `ProvideModule`. Se o host retorna o mesmo valor de identificador para o outro `IStream`, o CLR verifica se o conteúdo de fluxo já foi mapeado. Nesse caso, o CLR carrega a cópia existente da imagem em vez de mapeamento de um novo. Portanto, o identificador também não deve sobrepor os identificadores de assembly retornados de `ProvideAssembly`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
