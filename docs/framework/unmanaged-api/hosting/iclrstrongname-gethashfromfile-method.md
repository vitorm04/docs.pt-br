---
title: Método ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ed735c3d7830551581df35793f3f6fdc4953dc8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178068"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>Método ICLRStrongName::GetHashFromFile
Gera um hash sobre o conteúdo do arquivo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szFilePath`  
 [em] O nome do arquivo para hash.  
  
 `piHashAlg`  
 [dentro, fora] O algoritmo para usar ao gerar o hash. Algoritmos válidos são aqueles definidos pelo Win32 CryptoAPI. Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.  
  
 `pbHash`  
 [fora] Uma matriz de byte contendo o hash gerado.  
  
 `cchHash`  
 [em] O tamanho máximo do `pbHash` buffer que aponta para.  
  
 `pchHash`  
 [fora] O tamanho, em bytes, `pbHash`do devolvido.  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 Este método é o mesmo que o método [ICLRStrongName::GetHashFromFileW,](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) exceto que a especificação do nome do arquivo é ANSI em vez de Unicode.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
