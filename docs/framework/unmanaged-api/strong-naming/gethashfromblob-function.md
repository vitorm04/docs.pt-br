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
ms.openlocfilehash: 3d9e7b52c9061a1a7b470f9d4abf735e605087dc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352068"
---
# <a name="gethashfromblob-function"></a>Função GetHashFromBlob

Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.

Essa função foi preterida. Use o [iclrstrongname:: Gethashfromblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) método em vez disso.

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
[in] Um ponteiro para o endereço do bloco de memória a ser transformada em hash.

`cchBlob`\
[in] O comprimento, em bytes, do bloco de memória.

`piHashAlg`\
[no, out] Uma constante que especifica o algoritmo de hash. Use zero para o algoritmo padrão.

`pbHash`\
[out] O buffer de hash retornado.

`cchHash`\
[in] O tamanho máximo solicitado de `pbHash`.

`pchHash`\
[out] O tamanho, em bytes, do retornado `pbHash`.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** StrongName.h

**Biblioteca:** Incluído como um recurso em mscoree. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Método GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)