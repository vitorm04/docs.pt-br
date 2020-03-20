---
title: Função GetHashFromFileW
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175077"
---
# <a name="gethashfromfilew-function"></a>Função GetHashFromFileW
Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.  
  
 Esta função foi preterida. Use o método [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) em vez disso.  
  
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
  
## <a name="remarks"></a>Comentários  
 Esta função é a mesma [do GetHashFromFile,](gethashfromfile-function.md)exceto que a especificação do nome do arquivo é Unicode em vez de ANSI.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [Método GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
