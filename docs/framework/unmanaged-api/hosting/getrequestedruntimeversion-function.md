---
title: Função GetRequestedRuntimeVersion
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ee737f4c6d34e77996f5ba08ce4d84132a99238
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985654"
---
# <a name="getrequestedruntimeversion-function"></a>Função GetRequestedRuntimeVersion
Obtém o número de versão do common language runtime (CLR) solicitado pelo aplicativo especificado. Se essa versão não estiver instalado, obtém a versão mais recente instalado antes da versão solicitada.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pExe`  
 [in] O nome do aplicativo.  
  
 `pVersion`  
 [out] Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.  
  
 `cchBuffer`  
 [in] O comprimento do buffer de versão.  
  
 `pdwLength`  
 [out] Um ponteiro para o comprimento da sequência de números de versão.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro padrão (COM Component Object Model), conforme definido em Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|ERROR_INSUFFICIENT_BUFFER|O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.|  
|E_POINTER|`pdwLength` é nulo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [Função GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
