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
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176364"
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
  
## <a name="parameters"></a>parâmetros  
 `wszFilePath`  
 [em] O nome Unicode do arquivo para hash.  
  
 `piHashAlg`  
 [dentro, fora] O algoritmo para usar ao gerar o hash. Algoritmos válidos são aqueles definidos pelo Win32 CryptoAPI. Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.  
  
 `pbHash`  
 [fora] Uma matriz de byte contendo o hash gerado.  
  
 `cchHash`  
 [em] O tamanho máximo do buffer `pbHash`apontado por .  
  
 `pchHash`  
 [fora] O tamanho, em bytes, de `pbHash`.  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 Este método é o mesmo que o método [ICLRStrongName::GetHashFromFile,](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) exceto que a especificação do nome do arquivo é Unicode em vez de ANSI.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
