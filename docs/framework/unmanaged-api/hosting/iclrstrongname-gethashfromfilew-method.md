---
title: Método ICLRStrongName::GetHashFromFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: e5821abed4d6c7f7595bad3240ab86d5a128d794
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901156"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a>Método ICLRStrongName::GetHashFromFileW
Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 no O nome Unicode do arquivo para hash.  
  
 `piHashAlg`  
 [entrada, saída] O algoritmo a ser usado ao gerar o hash. Os algoritmos válidos são aqueles definidos pelo CryptoAPI do Win32. Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 será usado.  
  
 `pbHash`  
 fora Uma matriz de bytes que contém o hash gerado.  
  
 `cchHash`  
 no O tamanho máximo do buffer apontado por `pbHash`.  
  
 `pchHash`  
 fora O tamanho, em bytes, de `pbHash`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 Esse método é o mesmo que o método [ICLRStrongName:: GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , exceto que a especificação de nome de arquivo é Unicode em vez de ANSI.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
