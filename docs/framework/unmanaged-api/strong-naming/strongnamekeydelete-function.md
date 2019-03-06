---
title: Função StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc785a48d0cdf1cf2fdc0245a27b8ef35fd2d81
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364505"
---
# <a name="strongnamekeydelete-function"></a>Função StrongNameKeyDelete

Exclui o contêiner de chave especificado.

Essa função foi preterida. Use o [iclrstrongname:: Strongnamekeydelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) método em vez disso.

## <a name="syntax"></a>Sintaxe

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a>Parâmetros

`wszKeyContainer`\
[in] O nome de excluir o contêiner de chaves.

## <a name="return-value"></a>Valor de retorno

`true` Após a conclusão bem-sucedida; Caso contrário, `false`.

## <a name="remarks"></a>Comentários

Use o [StrongNameKeyInstall](strongnamekeyinstall-function.md) função para importar um par de chaves pública/privada para um contêiner.

Se o `StrongNameKeyDelete` função não for concluída com êxito, chame o [StrongNameErrorInfo](strongnameerrorinfo-function.md) função para recuperar o último erro gerado.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** StrongName.h

**Biblioteca:** Incluído como um recurso em mscoree. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Método StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [Método StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)