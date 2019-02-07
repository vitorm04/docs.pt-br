---
title: Método IXCLRDataMethodInstance::GetRepresentativeEntryAddress
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 52b2fdaaefd16a49300641f44041b8352141385b
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828586"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a>Método IXCLRDataMethodInstance::GetRepresentativeEntryAddress

Obtém o endereço do ponto de entrada mais representativo para a compilação nativa de todos os pontos de entrada possíveis para um método.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

### <a name="parameters"></a>Parâmetros

`addr` [out] O endereço do ponto de entrada nativo mais representativo para o método.

## <a name="remarks"></a>Comentários

O método fornecido faz parte de [ `IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) e corresponde ao slot de 19 da tabela de método virtual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também

- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Interface IXCLRDataMethodInstance](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
