---
title: Método ISOSDacInterface::GetMethodDescPtrFromIP
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: cd256250021436e611142de11c3625a21aeec814
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764747"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>Método ISOSDacInterface::GetMethodDescPtrFromIP

Recupera o ponteiro do MethodDesc correspondente o método que contém o endereço de determinada instrução nativos.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a>Parâmetros

`ip`\
[in] Um endereço dentro do método em tempo de execução.

`ppMD`\
[out] O endereço do `MethodDesc` para o método específico.

## <a name="remarks"></a>Comentários

O método fornecido faz parte dos [ `ISOSDacInterface` interface](isosdacinterface-interface.md) e corresponde ao slot de 21 da tabela de método virtual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também

- [Depuração](index.md)
- [ISOSDacInterface Interface](isosdacinterface-interface.md)
