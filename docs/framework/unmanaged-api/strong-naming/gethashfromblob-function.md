---
title: Função GetHashFromBlob
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140716"
---
# <a name="gethashfromblob-function"></a>Função GetHashFromBlob

Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.

Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) .

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a>Parâmetros

`pbBlob`\
no Um ponteiro para o endereço do bloco de memória com hash.

`cchBlob`\
no O comprimento, em bytes, do bloco de memória.

`piHashAlg`\
[entrada, saída] Uma constante que especifica o algoritmo de hash. Use zero para o algoritmo padrão.

`pbHash`\
fora O buffer de hash retornado.

`cchHash`\
no O tamanho máximo solicitado de `pbHash`.

`pchHash`\
fora O tamanho, em bytes, do `pbHash`retornado.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** StrongName. h

**Biblioteca:** Incluído como um recurso em MsCorEE. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Método GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
