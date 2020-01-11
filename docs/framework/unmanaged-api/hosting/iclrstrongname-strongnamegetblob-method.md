---
title: Método ICLRStrongName::StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: c7f04364cc52bd38d7d2659d1d188c5fd783ad01
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899758"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a>Método ICLRStrongName::StrongNameGetBlob
Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 no Um caminho válido para o arquivo executável a ser carregado.  
  
 `pbBlob`  
 no O buffer no qual carregar o arquivo executável.  
  
 `pcbBlob`  
 [entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob`. No retorno, o tamanho real, em bytes, de `pbBlob`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
