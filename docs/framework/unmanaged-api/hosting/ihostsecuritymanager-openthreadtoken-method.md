---
title: Método IHostSecurityManager::OpenThreadToken
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176260"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>Método IHostSecurityManager::OpenThreadToken
Abre o token de acesso discricionário associado ao segmento de execução atualmente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `dwDesiredAccess`  
 [em] Uma máscara de valores de acesso que especificam os tipos de acesso solicitados ao token de segmento. Esses valores são definidos `OpenThreadToken` na função Win32. Os tipos de acesso solicitados são conciliados com a lista de controle de acesso discricionário (DACL) do token para determinar quais tipos de acesso conceder ou negar.  
  
 `bOpenAsSelf`  
 [em] `true` especificar que a verificação de acesso deve ser feita usando o contexto de segurança do processo para o segmento de chamada; `false` para especificar que a verificação de acesso deve ser realizada usando o contexto de segurança do próprio segmento de chamada. Se o segmento está se passando por um cliente, o contexto de segurança pode ser o de um processo de cliente.  
  
 `phThreadToken`  
 [fora] Um ponteiro para o token de acesso recém-aberto.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`retornou com sucesso.|  
|Host_e_clrnotavailable|O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.|  
|HOST_E_TIMEOUT|A chamada acabou.|  
|HOST_E_NOT_OWNER|O interlocutor não é dono da fechadura.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.|  
|E_FAIL|Uma falha catastrófica desconhecida ocorreu. Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo. Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 `IHostSecurityManager::OpenThreadToken`comporta-se de forma semelhante à função Win32 correspondente de mesmo nome, exceto que a função Win32 `IHostSecurityManager::OpenThreadToken` permite que o chamador passe em uma alça para um segmento arbitrário, enquanto abre apenas o token associado ao segmento de chamada.  
  
 O `HANDLE` tipo não é compatível com COM, ou seja, seu tamanho é específico para o sistema operacional, e requer empacotamento personalizado. Assim, este token é para uso apenas dentro do processo, entre o CLR e o host.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Interface IHostSecurityManager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
