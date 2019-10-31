---
title: Método ICLRRuntimeInfo::LoadErrorString
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
ms.openlocfilehash: 20f2041599e85b8df20a7a9cf44680da9f17244e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195938"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a>Método ICLRRuntimeInfo::LoadErrorString
Traduz um valor HRESULT em uma mensagem de erro apropriada para a cultura especificada.  
  
 Esse método substitui as seguintes funções:  
  
- [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iResourceID`  
 no O HRESULT a ser traduzido.  
  
 `pwzBuffer`  
 fora A cadeia de caracteres da mensagem associada ao HRESULT fornecido.  
  
 `pcchBuffer`  
 [entrada, saída] O tamanho de `pwzbuffer` para evitar estouros de buffer. Se `pwzbuffer` for NULL, `pcchBuffer` fornecerá o tamanho esperado de `pwzbuffer` para permitir a prealocação.  
  
 `iLocaleID`  
 no O identificador de cultura. Para usar a cultura padrão, você deve especificar-1.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pcchBuffer` é nulo.|  
|E_INVALIDARG|`pwzBuffer` é nulo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
