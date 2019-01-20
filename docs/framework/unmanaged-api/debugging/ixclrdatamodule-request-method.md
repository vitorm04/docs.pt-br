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
ms.openlocfilehash: 0226a11b142515296d976e3d645cb2475d634420
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416272"
---
# <a name="ixclrdatamodulerequest-method"></a>Método IXCLRDataModule::Request

Solicitações para preencher o buffer fornecido com os dados do módulo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

### <a name="parameters"></a>Parâmetros

`reqCode` [in] Tipo a ser enviado de solicitação.

`inBufferSize` [in] o tamanho do buffer de entrada a ser passado.

`inBuffer` [in, size_is(inBufferSize)] Ponteiro de buffer para os dados brutos a serem enviados na solicitação.

`outBufferSize` [in] Tamanho do buffer de saída.

`outBuffer` [out, size_is(outBufferSize)] Ponteiro de buffer usado para armazenar a resposta da solicitação.

## <a name="remarks"></a>Comentários

O método fornecido é parte do `IXCLRDataModule` de interface e corresponde ao slot de 36 ª da tabela de método virtual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum   
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também
- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Interface IXCLRDataModule](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
