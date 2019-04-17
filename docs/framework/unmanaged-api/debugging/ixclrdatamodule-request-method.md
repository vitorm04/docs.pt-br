---
title: Método IXCLRDataModule::Request
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 755063ca6da29a2e4733dd653306192ac0434ec0
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610594"
---
# <a name="ixclrdatamodulerequest-method"></a>Método IXCLRDataModule::Request

Solicitações para preencher o buffer fornecido com os dados do módulo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>Parâmetros

`reqCode`\
[in] Tipo a ser enviado de solicitação.

`inBufferSize`\
[in] o tamanho do buffer de entrada a ser passado.

`inBuffer`\
[in, size_is(inBufferSize)] Ponteiro de buffer para os dados brutos a serem enviados na solicitação.

`outBufferSize`\
[in] Tamanho do buffer de saída.

`outBuffer`\
[out, size_is(outBufferSize)] Ponteiro de buffer usado para armazenar a resposta da solicitação.

## <a name="remarks"></a>Comentários

O método fornecido é parte do `IXCLRDataModule` de interface e corresponde ao slot de 36 ª da tabela de método virtual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).
**Cabeçalho:** Nenhum **biblioteca:** Nenhum **versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Consulte também

- [Depuração](index.md)
- [Interface IXCLRDataModule](ixclrdatamodule-interface.md)