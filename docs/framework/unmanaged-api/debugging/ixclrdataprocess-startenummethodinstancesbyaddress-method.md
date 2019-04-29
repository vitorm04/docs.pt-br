---
title: Método IXCLRDataProcess::StartEnumMethodInstancesByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 41b6ff0a3c44d3ad997c54b1c82590cc3583fe52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775226"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a>Método IXCLRDataProcess::StartEnumMethodInstancesByAddress

Fornece um identificador para enumerar as instâncias do método de `AppDomain` começando em um determinado endereço.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a>Parâmetros

`address`\
[in] O endereço da primeira instância de método.

`appDomain`\
[in] O AppDomain das instâncias do método.

`handle`\
[out] Um identificador para enumerar as instâncias de método.

## <a name="remarks"></a>Comentários

O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 27 da tabela de método virtual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também

- [Enumeração CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Depuração](index.md)
- [Interface IXCLRDataProcess](ixclrdataprocess-interface.md)
