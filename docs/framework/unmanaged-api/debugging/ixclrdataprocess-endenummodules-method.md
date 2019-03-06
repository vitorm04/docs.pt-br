---
title: Método IXCLRDataProcess::EndEnumModules
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3b7050e92af6fc58b45837840b2796a5deac955c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375331"
---
# <a name="ixclrdataprocessendenummodules-method"></a>Método IXCLRDataProcess::EndEnumModules

Libera os recursos usados pelos iteradores internos usados durante a enumeração de módulo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe
```
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>Parâmetros

`handle`\
[out] Um identificador para enumerar os módulos.

## <a name="remarks"></a>Comentários

O método fornecido é parte do `IXCLRDataProcess` de interface e corresponde ao slot de 26 da tabela de método virtual.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).   
**Cabeçalho:** Nenhum   
**Biblioteca:** Nenhum   
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   

## <a name="see-also"></a>Consulte também

- [Depuração](index.md)
- [Interface IXCLRDataProcess](ixclrdataprocess-interface.md)
