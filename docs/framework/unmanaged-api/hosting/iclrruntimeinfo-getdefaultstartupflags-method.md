---
title: "Método ICLRRuntimeInfo::GetDefaultStartupFlags"
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
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8b278a791c7e5418322a80bc6478f75791a35af8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>Método ICLRRuntimeInfo::GetDefaultStartupFlags
Obtém os sinalizadores de inicialização e o arquivo de configuração de host que será usado para iniciar o tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwStartupFlags`  
 [out] Um ponteiro para os sinalizadores de inicialização do host que estão atualmente definidas.  
  
 `pwzHostConfigFile`  
 [out] Um ponteiro para o caminho do diretório do arquivo de configuração de host atual.  
  
 `pcchHostConfigFile`  
 [out no] Na entrada, o tamanho de `pwzHostConfigFile`, para evitar estouros de buffer. Se `pwzHostConfigFile` é null, o método retorna o tamanho necessário do `pwzHostConfigFile` de pré-alocação.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
  
## <a name="remarks"></a>Comentários  
 Este método retorna os valores de sinalizador padrão (`STARTUP_CONCURRENT_GC` e `NULL`), ou os valores fornecidos por uma chamada anterior a [: Setdefaultstartupflags método](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), ou os valores definidos por qualquer uma da `CorBind*` métodos se eles estiverem associados a esse tempo de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
