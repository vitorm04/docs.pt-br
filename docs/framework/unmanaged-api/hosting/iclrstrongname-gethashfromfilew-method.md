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
ms.openlocfilehash: 6dbb3360132186c38c007fb5fa12a3724ca145aa
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762091"
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
 no O tamanho máximo do buffer apontado por `pbHash` .  
  
 `pchHash`  
 fora O tamanho, em bytes, de `pbHash` .  
  
## <a name="return-value"></a>Valor Retornado  
 `S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 Esse método é o mesmo que o método [ICLRStrongName:: GetHashFromFile](iclrstrongname-gethashfromfile-method.md) , exceto que a especificação de nome de arquivo é Unicode em vez de ANSI.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetHashFromFile](iclrstrongname-gethashfromfile-method.md)
- [Interface ICLRStrongName](iclrstrongname-interface.md)
