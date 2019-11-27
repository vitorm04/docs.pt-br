---
title: Enumeração CorThreadSafetyOptions
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 93dd8c56176890d04d792f3c336492e4f232825b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442474"
---
# <a name="corthreadsafetyoptions-enumeration"></a>Enumeração CorThreadSafetyOptions

Especifica sinalizadores para selecionar opções para a segurança do thread.

## <a name="syntax"></a>Sintaxe

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>Membros

|{1&gt;Membro&lt;1}|Descrição|
|------------|-----------------|
|`MDThreadSafetyDefault`|Valor padrão. Mesmo que `MDThreadSafetyOff`.|
|`MDThreadSafetyOff`|Indica que um bloqueio de leitor/gravador não pode ser definido.|
|`MDThreadSafetyOn`|Indica que um bloqueio de leitor/gravador pode ser definido.|

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** CorHdr. h

**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
