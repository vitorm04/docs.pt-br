---
title: Função StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3fc69b2edf611383402b13555cf33be10dbad3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366576"
---
# <a name="strongnamekeyinstall-function"></a>Função StrongNameKeyInstall

Importa um par de chaves públicas/privadas em um contêiner.

Essa função foi preterida. Use o [iclrstrongname:: Strongnamekeyinstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) método em vez disso.

## <a name="syntax"></a>Sintaxe

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a>Parâmetros

`wszKeyContainer`\
[in] O nome do contêiner de chave. `wszKeyContainer` deve ser uma cadeia de caracteres não vazia.

`pbKeyBlob`\
[in] O par de chaves binário.

`cbKeyBlob`\
[in] O tamanho, em bytes, do `pbKeyBlob`.

## <a name="return-value"></a>Valor de retorno

`true` Após a conclusão bem-sucedida; Caso contrário, `false`.

## <a name="remarks"></a>Comentários

Use o [StrongNameKeyDelete](strongnamekeydelete-function.md) função para excluir o contêiner de chave.

Se o `StrongNameKeyInstall` função não for concluída com êxito, chame o [StrongNameErrorInfo](strongnameerrorinfo-function.md) função para recuperar o último erro gerado.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** StrongName.h

**Biblioteca:** Incluído como um recurso em mscoree. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Método StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [Método StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)