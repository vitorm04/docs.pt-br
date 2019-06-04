---
title: Função LockClrVersion
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dd1b895abbd2357c46361c6381b1625422403f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490192"
---
# <a name="lockclrversion-function"></a>Função LockClrVersion
Permite que o host determine qual versão do common language runtime (CLR) será usado dentro do processo antes de inicializar explicitamente o CLR.  
  
 Essa função foi preterida no .NET Framework 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `hostCallback`  
 [in] A função a ser chamado pelo CLR na inicialização.  
  
 `pBeginHostSetup`  
 [in] A função a ser chamado pelo host para informar ao CLR que a inicialização está sendo iniciado.  
  
 `pEndHostSetup`  
 [in] A função a ser chamado pelo host para informar ao CLR que a inicialização foi concluída.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|Um ou mais dos argumentos é nulo.|  
  
## <a name="remarks"></a>Comentários  
 O host chama `LockClrVersion` antes de inicializar o CLR. `LockClrVersion` usa três parâmetros, que são os retornos de chamada do tipo [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Esse tipo é definido da seguinte maneira.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 As seguintes etapas ocorrem após a inicialização do tempo de execução:  
  
1. O host chama [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou uma das outras funções de inicialização de tempo de execução. Como alternativa, o host foi possível inicializar o tempo de execução usando a ativação de objeto COM.  
  
2. O tempo de execução chama a função especificada pelo `hostCallback` parâmetro.  
  
3. A função especificada por `hostCallback` , em seguida, faz a seguinte sequência de chamadas:  
  
    - A função especificada pelo `pBeginHostSetup` parâmetro.  
  
    - `CorBindToRuntimeEx` (ou outra função de inicialização de tempo de execução).  
  
    - [ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    - A função especificada pelo `pEndHostSetup` parâmetro.  
  
 Todas as chamadas de `pBeginHostSetup` para `pEndHostSetup` deve ocorrer em um único thread ou fibra, com a mesma pilha de lógica. Esse thread pode ser diferente do thread no qual `hostCallback` é chamado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
