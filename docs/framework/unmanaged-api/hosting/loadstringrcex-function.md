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
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177978"
---
# <a name="loadstringrcex-function"></a>Função LoadStringRCEx
Traduz um valor HRESULT para uma mensagem de erro apropriada para a cultura especificada.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `lcid`  
 [em] Um identificador de cultura. Passe -1 `lcid` para usar a cultura padrão.  
  
 `iResourceID`  
 [em] Um HRESULT.  
  
 `szBuffer`  
 [fora] Um buffer que contém a mensagem de erro após a conclusão bem sucedida.  
  
 `iMax`  
 [em] O tamanho do buffer de mensagem de erro.  
  
 `bQuiet`  
 [em] Ignorado.  
  
 `pcwchUsed`  
 [fora] Um ponteiro para o comprimento da mensagem de erro.  
  
## <a name="return-value"></a>Valor retornado  
 Este método retorna códigos de erro COM padrão, conforme definido em WinError.h, além dos seguintes valores.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com sucesso.|  
|E_INVALIDARG|`szBuffer`é nulo, ou `iMax` é zero (0).|  
  
## <a name="remarks"></a>Comentários  
 Se o método não `szBuffer` for concluído com sucesso, contém uma seqüência vazia.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [Função LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
