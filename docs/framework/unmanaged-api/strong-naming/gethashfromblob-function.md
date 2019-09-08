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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4df08157ce14a58393e54b671e8f41b8998ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799237"
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
fora O tamanho, em bytes, do retornado `pbHash`.

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).

**Cabeçalho:** StrongName.h

**Biblioteca** Incluído como um recurso em MsCorEE. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Método GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
