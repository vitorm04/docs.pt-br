---
title: Método ISOSDacInterface::GetModuleData
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b0edd459deaf68040e05209c6ecf2cb7cae12e8d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369945"
---
# <a name="isosdacinterfacegetmoduledata-method"></a>Método ISOSDacInterface::GetModuleData

Busca os dados correspondentes para o módulo carregado em um determinado endereço.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

### <a name="parameters"></a>Parâmetros

`moduleAddr`\
[in] O endereço do módulo para recuperar informações para.

`data`\
[out] O [DacpModuleData estrutura](dacpmoduledata-structure.md) para conter as informações do módulo carregado.


## <a name="remarks"></a>Comentários

O método fornecido é parte do `ISOSDacInterface` de interface e corresponde ao slot de 13 da tabela de método virtual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também

- [Depuração](index.md)
- [ISOSDacInterface Interface](isosdacinterface-interface.md)