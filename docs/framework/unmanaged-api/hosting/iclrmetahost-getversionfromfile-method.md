---
title: Método ICLRMetaHost::GetVersionFromFile
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 538e596c3a705020150f52c9e55605a49434ce8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetahostgetversionfromfile-method"></a>Método ICLRMetaHost::GetVersionFromFile
Obtém do .NET Framework compilação versão original um assembly (armazenado nos metadados), dado seu caminho de arquivo. Esse método substitui o [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwzFilePath`  
 [in] O caminho do arquivo de assembly completo.  
  
 `pwzbuffer`  
 [out] A versão de compilação do .NET Framework armazenada nos metadados, no formato "v*um*. *B*[. *X*] ". *Um*, *B*, e *X* são números decimais que correspondem a versão principal, a versão secundária, e o número de compilação. O comprimento da cadeia de caracteres é limitado a MAX_PATH.  
  
> [!NOTE]
>  Essa saída corresponde ao nome de diretório para a versão do .NET Framework, como ele aparece em C:\Windows\Microsoft.NET\Framework.  
  
 Os valores de exemplo são "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" e "v 4.0. *X*", onde *X* depende do número de compilação instalado. Observe que o prefixo "v" é necessário.  
  
 `pcchBuffer`  
 [out no] O tamanho de `pwzbuffer` para evitar estouros de buffer.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pwzbuffer` ou `pcchBuffer` é nulo.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|O buffer é muito pequeno.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
