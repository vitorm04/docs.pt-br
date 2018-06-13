---
title: Método ICLRRuntimeInfo::GetRuntimeDirectory
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetRuntimeDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f366e736c90ffd8cf588af3a6e5f6240426b9980
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434519"
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>Método ICLRRuntimeInfo::GetRuntimeDirectory
Obtém o diretório de instalação do common language runtime (CLR) associado a esta interface.  
  
 Esse método substitui o [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) função fornecido nas versões do .NET Framework 2.0, 3.0 e 3.5.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzBuffer`  
 [out] Retorna o diretório de instalação do CLR. O caminho de instalação é totalmente qualificado; Por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705\\".  
  
 `pchBuffer`  
 [out no] Especifica o tamanho do `pwzBuffer` para evitar estouros de buffer. Se `pwzBuffer` for nulo, `pchBuffer` retorna o tamanho necessário do `pwzBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pwzBuffer` ou `pchBuffer` é nulo.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
