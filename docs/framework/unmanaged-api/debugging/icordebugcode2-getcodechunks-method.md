---
title: Método ICorDebugCode2::GetCodeChunks
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
ms.openlocfilehash: e419ebb6ffd404368baf32e591e08c4a70645127
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121116"
---
# <a name="icordebugcode2getcodechunks-method"></a>Método ICorDebugCode2::GetCodeChunks

Obtém as partes de código das quais este objeto de código é composto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a>Parâmetros

`cbufSize`  
no Tamanho da matriz de `chunks`.

`pcnumChunks`  
fora O número de partes retornadas na matriz de `chunks`.

`chunks`  
fora Uma matriz de estruturas "CodeChunkInfo", cada uma representando uma única parte do código. Se o valor de `cbufSize` for 0, esse parâmetro poderá ser nulo.

## <a name="remarks"></a>Comentários

Os trechos de código nunca serão sobrepostos e eles seguirão a ordem em que seriam concatenados por [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md). Um objeto de código MSIL (Microsoft Intermediate Language) no .NET Framework versão 2,0 incluirá uma única parte de código.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

**Cabeçalho:** CorDebug.idl, CorDebug.h

**Biblioteca:** CorGuids.lib

**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
