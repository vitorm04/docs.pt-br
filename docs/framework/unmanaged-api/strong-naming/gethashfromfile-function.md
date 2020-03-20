---
title: Função GetHashFromFile
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176975"
---
# <a name="gethashfromfile-function"></a>Função GetHashFromFile
Gera um hash sobre o conteúdo do arquivo especificado.  
  
 Esta função foi preterida. Use o método [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) em vez disso.  
  
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
  
## <a name="remarks"></a>Comentários  
 Esta função é a mesma [de GetHashFromFileW,](gethashfromfilew-function.md)exceto que a especificação do nome do arquivo é ANSI em vez de Unicode.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md)
- [Método GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
