---
title: Função StrongNameSignatureSize
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176884"
---
# <a name="strongnamesignaturesize-function"></a>Função StrongNameSignatureSize
Retorna o tamanho da assinatura de nome forte. `StrongNameSignatureSize`é normalmente usado por compiladores para determinar quanto espaço reservar no arquivo ao criar um conjunto assinado por atraso.  
  
 Esta função foi preterida. Use o método [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a>parâmetros  
 `pbPublicKeyBlob`  
 [em] Uma estrutura do tipo [PublicKeyBlob](publickeyblob-structure.md) que contém a parte pública do par de chaves usada para gerar a assinatura de nome forte.  
  
 `cbPublicKeyBlob`  
 [em] O tamanho, em bytes, de `pbPublicKeyBlob`.  
  
 `pcbSize`  
 [em] O número de bytes necessários para armazenar a assinatura de nome forte.  
  
## <a name="return-value"></a>Valor retornado  
 `true`em conclusão bem sucedida; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se `StrongNameSignatureSize` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
