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
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176234"
---
# <a name="loadstringrc-function"></a>Função LoadStringRC
Traduz um valor HRESULT em uma mensagem de erro usando a cultura padrão do segmento atual.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `iResourceID`  
 [em] Um HRESULT.  
  
 `szBuffer`  
 [fora] Um buffer que contém a mensagem de erro após a conclusão bem sucedida.  
  
 `iMax`  
 [em] O tamanho do buffer de mensagem de erro.  
  
 `bQuiet`  
 [em] Ignorado.  
  
## <a name="return-value"></a>Valor retornado  
 Este método retorna códigos de erro com (Component Object Model, modelo de objeto componente padrão), conforme definido em WinError.h, além dos seguintes valores.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com sucesso.|  
|E_INVALIDARG|`szBuffer`é nulo ou `iMax` é zero (0).|  
  
## <a name="remarks"></a>Comentários  
 Se o método não `szBuffer` for concluído com sucesso, contém uma seqüência vazia.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll e Mscorwks.dll. Use o MSCorEE.dll em vez de Mscorwks.dll para garantir que você direcione a versão correta do .NET Framework.  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
