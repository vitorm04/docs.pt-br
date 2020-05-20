---
title: 'Método IXCLRDataProcess:: GetAppDomainByUniqueId'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bb02ffed09cbcc31e653bfd3165050c247908c5d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420771"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a>Método IXCLRDataProcess:: GetAppDomainByUniqueId

Obtém um `AppDomain` em um processo com base em seu identificador exclusivo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a>Parâmetros

`id`\
no O identificador exclusivo do AppDomain

`appDomain`\
fora O AppDomain

## <a name="remarks"></a>Comentários

O método fornecido faz parte da `IXCLRDataProcess` interface e corresponde ao slot 20 da tabela de métodos virtuais. O `IXCLRDataAppDomain*` retornado é usado para interação com outras APIs.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).
**Cabeçalho:** Nenhuma **biblioteca:** nenhuma **.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Interface IXCLRDataProcess](ixclrdataprocess-interface.md)
