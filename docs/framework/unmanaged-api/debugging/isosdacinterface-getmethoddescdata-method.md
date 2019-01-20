---
title: Método ISOSDacInterface::GetMethodDescData
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
ms.openlocfilehash: 3f22752446413c622a20340541b0ac328f63c77b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416312"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>Método ISOSDacInterface::GetMethodDescData

Obtém os dados para o determinado [MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md).

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a>Parâmetros

`methodDesc` [in] O endereço do MethodDesc.

`ip` [in] O endereço IP do método.

`data` [out] Os dados associados a MethodDesc conforme retornado pelo APIs internas. A estrutura precisa de pelo menos bytes 168.

`cRevertedRejitVersions` [out] O número de versões do rejit revertido.

`rgRevertedRejitData` [out] Os dados associados com as versões do rejit revertido como retornado pelo APIs internas. A estrutura precisa de pelo menos 24 bytes.

`pcNeededRevertedRejitData` [out] O número de bytes necessários para armazenar os dados associados com as versões do ReJit revertidas.

## <a name="remarks"></a>Comentários

O método fornecido é parte do `ISOSDacInterface` de interface e corresponde ao slot de 20 anos da tabela de método virtual. Também o `CLRDATA_ADDRESS` são inteiro sem sinal de 64 bits.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também

- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [ISOSDacInterface Interface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
