---
title: Método ICLRRuntimeInfo::GetDefaultStartupFlags
ms.date: 03/30/2017
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
ms.openlocfilehash: 0ce822533b0699f3467dc08044aa4dab59285a77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120310"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>Método ICLRRuntimeInfo::GetDefaultStartupFlags
Obtém os sinalizadores de inicialização e o arquivo de configuração do host que serão usados para iniciar o tempo de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pdwStartupFlags`  
 fora Um ponteiro para os sinalizadores de inicialização do host que estão atualmente definidos.  
  
 `pwzHostConfigFile`  
 fora Um ponteiro para o caminho do diretório do arquivo de configuração do host atual.  
  
 `pcchHostConfigFile`  
 [entrada, saída] Na entrada, o tamanho de `pwzHostConfigFile`para evitar estouros de buffer. Se `pwzHostConfigFile` for NULL, o método retornará o tamanho necessário de `pwzHostConfigFile` para pré-alocação.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna os valores de sinalizador padrão (`STARTUP_CONCURRENT_GC` e `NULL`) ou os valores fornecidos por uma chamada anterior para o [método ICLRRuntimeInfo:: SetDefaultStartupFlags](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)ou os valores definidos por qualquer um dos métodos de `CorBind*` se eles estiverem associados a esse tempo de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
