---
title: 'Método IXCLRDataProcess:: EndEnumMethodInstancesByAddress'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395253"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a>Método IXCLRDataProcess:: EndEnumMethodInstancesByAddress

Libera os recursos usados por iteradores internos usados durante a enumeração da instância.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>Parâmetros

`handle`\
fora Um identificador para enumerar as instâncias de método.

## <a name="remarks"></a>Comentários

O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 30 da tabela de métodos virtuais.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Enumeração CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Depuração](index.md)
- [Interface IXCLRDataProcess](ixclrdataprocess-interface.md)
