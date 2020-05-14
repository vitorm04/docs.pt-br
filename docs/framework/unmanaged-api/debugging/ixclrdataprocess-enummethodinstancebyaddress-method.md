---
title: 'Método IXCLRDataProcess:: EnumMethodInstanceByAddress'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: f3800a5980304394dd648111fe23a3bb0890c575
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395117"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>Método IXCLRDataProcess:: EnumMethodInstanceByAddress

Enumera as instâncias de método deste processo Iniciando em um deslocamento de endereço.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a>Parâmetros

`handle`\
no Um identificador para enumerar as instâncias de método.

`mod`\
fora A instância do método enumerado.

## <a name="remarks"></a>Comentários

O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot de 29 da tabela de métodos virtuais.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).
**Cabeçalho:** Nenhuma **biblioteca:** nenhuma **.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Veja também

- [Enumeração CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Depuração](index.md)
- [Interface IXCLRDataProcess](ixclrdataprocess-interface.md)
