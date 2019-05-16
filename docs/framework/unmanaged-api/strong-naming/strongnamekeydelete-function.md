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
ms.openlocfilehash: 717d2104db8addf40e5187cee4cc8c46e5dc355e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636734"
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
