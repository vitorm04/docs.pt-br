---
title: Estrutura PublicKeyBlob
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176949"
---
# <a name="publickeyblob-structure"></a>Estrutura PublicKeyBlob
Representa, em formato binário, a chave pública de um par de chaves público/privado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`SigAlgId`|O identificador para o algoritmo `ALG_ID`de assinatura (do tipo, conforme definido no WinCrypt.h) da chave pública.|  
|`HashAlgId`|O identificador para o algoritmo `ALG_ID`hash (do tipo , conforme definido no WinCrypt.h) da chave pública.|  
|`cbPublicKey`|O comprimento da chave em bytes.|  
|`PublicKey`|Uma matriz de byte de comprimento variável que contém o valor-chave no formato retornado pelo CryptoAPI.|  
  
## <a name="remarks"></a>Comentários  
 A `PublicKeyBlob` estrutura é usada por [StrongNameGetPublicKey,](strongnamegetpublickey-function.md) [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)e outras funções de nome forte para representar a chave pública de um par de chaves público/privado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função StrongNameGetPublicKey](strongnamegetpublickey-function.md)
- [Função StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)
