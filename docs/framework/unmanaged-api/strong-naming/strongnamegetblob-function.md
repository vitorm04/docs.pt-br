---
title: Função StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095008"
---
# <a name="strongnamegetblob-function"></a>Função StrongNameGetBlob
Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameGetBlob](../hosting/iclrstrongname-strongnamegetblob-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 no Um caminho válido para o arquivo executável a ser carregado.  
  
 `pbBlob`  
 no O buffer no qual carregar o arquivo executável.  
  
 `pcbBlob`  
 [entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob`. No retorno, o tamanho real, em bytes, de `pbBlob`.  
  
## <a name="return-value"></a>Valor retornado  
 `true` após a conclusão bem-sucedida; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se a função `StrongNameGetBlob` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameGetBlob](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [Método StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
