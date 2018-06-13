---
title: Função LoadStringRCEx
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38c942b9a94c83f5a3316cf3ae3ccbbad2b0ec69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444311"
---
# <a name="loadstringrcex-function"></a>Função LoadStringRCEx
Converte um valor HRESULT a uma mensagem de erro apropriada para a cultura especificada.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `lcid`  
 [in] Um identificador de cultura. Passe -1 para `lcid` para usar a cultura padrão.  
  
 `iResourceID`  
 [in] Um HRESULT.  
  
 `szBuffer`  
 [out] Um buffer que contém a mensagem de erro após a conclusão bem-sucedida.  
  
 `iMax`  
 [in] O tamanho do buffer de mensagem de erro.  
  
 `bQuiet`  
 [in] Ignorado.  
  
 `pcwchUsed`  
 [out] Um ponteiro para o comprimento da mensagem de erro.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro COM padrão, conforme definido no Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|`szBuffer` é nulo, ou `iMax` é zero (0).|  
  
## <a name="remarks"></a>Comentários  
 Se o método não for concluída com êxito, `szBuffer` contém uma cadeia de caracteres vazia.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>  
 [Função LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
