---
title: 'Método ISOSDacInterface:: GetMethodDescData'
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e4c44379d9db0f5e98f3ca66ec0486961ec2df3a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396942"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>Método ISOSDacInterface:: GetMethodDescData

Obtém os dados para o ponteiro MethodDesc fornecido.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>Parâmetros

`methodDesc`\
no O endereço do MethodDesc.

`ip`\
no O endereço IP do método.

`data`\
fora Os dados associados ao MethodDesc como retornados das APIs internas.

`cRevertedRejitVersions`\
fora O número de versões de ReJIT revertidas.

`rgRevertedRejitData`\
fora Os dados associados às versões de ReJIT revertidas, conforme retornado das APIs internas.

`pcNeededRevertedRejitData`\
fora O número de bytes necessários para armazenar os dados associados às versões de ReJit revertidas.

## <a name="remarks"></a>Comentários

O método fornecido faz parte da `ISOSDacInterface` interface e corresponde ao slot 21 da tabela de métodos virtuais. Para poder usá-los, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) deve ser definido como um inteiro sem sinal de 64 bits.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Interface ISOSDacInterface](isosdacinterface-interface.md)
