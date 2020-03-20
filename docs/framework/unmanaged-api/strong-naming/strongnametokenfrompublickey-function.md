---
title: Função StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175051"
---
# <a name="strongnametokenfrompublickey-function"></a>Função StrongNameTokenFromPublicKey
Obtém um token que representa uma chave pública. Um nome forte é a forma abreviada de uma chave pública.  
  
 Esta função foi preterida. Use o método [ICLRStrongName::StrongNameTokenFromPublicKey.](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pbPublicKeyBlob`  
 [em] Uma estrutura do tipo [PublicKeyBlob](publickeyblob-structure.md) que contém a parte pública do par de chaves usada para gerar a assinatura de nome forte.  
  
 `cbPublicKeyBlob`  
 [em] O tamanho, em bytes, de `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [fora] O token de nome forte `pbPublicKeyBlob`correspondente à chave passou em . O tempo de execução do idioma comum aloca a memória na qual o token retorna. O chamador deve liberar essa memória usando a função [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbStrongNameToken`  
 [fora] O tamanho, em bytes, do nome forte devolvido token.  
  
## <a name="return-value"></a>Valor retornado  
 `true`em conclusão bem sucedida; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Um token de nome forte é a forma abreviada de uma chave pública usada para economizar espaço ao armazenar informações-chave em metadados. Especificamente, tokens de nome fortes são usados em referências de montagem para se referir ao conjunto dependente.  
  
 Se `StrongNameTokenFromPublicKey` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [Método StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [Estrutura PublicKeyBlob](publickeyblob-structure.md)
