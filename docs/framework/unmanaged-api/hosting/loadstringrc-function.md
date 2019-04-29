---
title: Função LoadStringRC
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f17ecfe683de0739e4e1e063d38836eecf949336
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765304"
---
# <a name="loadstringrc-function"></a>Função LoadStringRC
Converte um valor HRESULT em uma mensagem de erro usando a cultura padrão do thread atual.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iResourceID`  
 [in] Um HRESULT.  
  
 `szBuffer`  
 [out] Um buffer que contém a mensagem de erro após a conclusão bem-sucedida.  
  
 `iMax`  
 [in] O tamanho do buffer de mensagem de erro.  
  
 `bQuiet`  
 [in] Ignorado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro padrão (COM Component Object Model), conforme definido em Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|`szBuffer` é nulo ou `iMax` é zero (0).|  
  
## <a name="remarks"></a>Comentários  
 Se o método não for concluída com êxito, `szBuffer` contém uma cadeia de caracteres vazia.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree. dll e mscorwks. dll. Use mscoree. dll em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
