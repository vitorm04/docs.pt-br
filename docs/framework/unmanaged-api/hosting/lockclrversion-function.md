---
title: "Função LockClrVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LockClrVersion
helpviewer_keywords: LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a58d7e99f545026f6f133901ef35a1f9b9fabc7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lockclrversion-function"></a>Função LockClrVersion
Permite que o host determinar qual versão do common language runtime (CLR) será usado no processo antes de inicializar explicitamente o CLR.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hostCallback`  
 [in] A função a ser chamada pelo CLR na inicialização.  
  
 `pBeginHostSetup`  
 [in] A função a ser chamado pelo host para informar ao CLR que a inicialização está iniciando.  
  
 `pEndHostSetup`  
 [in] A função a ser chamado pelo host para informar ao CLR que a inicialização for concluída.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro COM padrão, conforme definido no Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|Um ou mais dos argumentos for nulo.|  
  
## <a name="remarks"></a>Comentários  
 As chamadas de host `LockClrVersion` antes de inicializar o CLR. `LockClrVersion`usa três parâmetros, que são chamadas de retorno do tipo [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Esse tipo é definido da seguinte maneira.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 As seguintes etapas ocorrem na inicialização do tempo de execução:  
  
1.  As chamadas de host [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou uma das outras funções de inicialização de tempo de execução. Como alternativa, o host foi possível inicializar o tempo de execução usando a ativação de objeto COM.  
  
2.  O tempo de execução chama a função especificada pelo `hostCallback` parâmetro.  
  
3.  A função especificada por `hostCallback` , em seguida, faz com que a seguinte sequência de chamadas:  
  
    -   A função especificada pelo `pBeginHostSetup` parâmetro.  
  
    -   `CorBindToRuntimeEx`(ou outra função de inicialização do tempo de execução).  
  
    -   [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    -   [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    -   A função especificada pelo `pEndHostSetup` parâmetro.  
  
 Todas as chamadas de `pBeginHostSetup` para `pEndHostSetup` devem ocorrer em um único thread ou fibra, com a mesma pilha de lógica. Esse thread pode ser diferente do thread no qual `hostCallback` é chamado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
