---
title: Função StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b99b29a85f498a6bfa0363a446bf589876bff9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799090"
---
# <a name="strongnamegetblobfromimage-function"></a>Função StrongNameGetBlobFromImage
Obtém uma representação binária da imagem do assembly no endereço de memória especificado.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbBase`  
 no O endereço de memória do manifesto do assembly mapeado.  
  
 `dwLength`  
 no O tamanho, em bytes, da imagem em `pbBase`.  
  
 `pbBlob`  
 no Um buffer para conter a representação binária da imagem.  
  
 `pcbBlob`  
 [entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob`. No retorno, o tamanho real, em bytes, de `pbBlob`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`após a conclusão bem-sucedida; caso contrário `false`,.  
  
## <a name="remarks"></a>Comentários  
 Se a `StrongNameGetBlobFromImage` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [Método StrongNameGetBlob](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
