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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799221"
---
# <a name="gethashfromfile-function"></a>Função GetHashFromFile
Gera um hash sobre o conteúdo do arquivo especificado.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) .  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `szFilePath`  
 no O nome do arquivo para hash.  
  
 `piHashAlg`  
 [entrada, saída] O algoritmo a ser usado ao gerar o hash. Os algoritmos válidos são aqueles definidos pelo CryptoAPI do Win32. Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 será usado.  
  
 `pbHash`  
 fora Uma matriz de bytes que contém o hash gerado.  
  
 `cchHash`  
 no O tamanho máximo do buffer que `pbHash` aponta para.  
  
 `pchHash`  
 fora O tamanho, em bytes, do retornado `pbHash`.  
  
## <a name="remarks"></a>Comentários  
 Essa função é a mesma que [GetHashFromFileW](gethashfromfilew-function.md), exceto que a especificação de nome de arquivo é ANSI em vez de Unicode.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md)
- [Método GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
