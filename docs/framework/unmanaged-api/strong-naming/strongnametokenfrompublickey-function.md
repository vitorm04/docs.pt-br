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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb8ff76da288975ef291d226bb1f205e73a64252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="strongnametokenfrompublickey-function"></a>Função StrongNameTokenFromPublicKey
Obtém um token que representa uma chave pública. Um token de nome forte é a forma abreviada de uma chave pública.  
  
 Essa função foi preterida. Use o [: Strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbPublicKeyBlob`  
 [in] Uma estrutura de tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.  
  
 `cbPublicKeyBlob`  
 [in] O tamanho, em bytes, de `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] O token de nome forte correspondente à chave passada `pbPublicKeyBlob`. O common language runtime aloca a memória no qual retornar o token. O chamador deve liberar esta memória usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.  
  
 `pcbStrongNameToken`  
 [out] O tamanho, em bytes, do token retornado de nome forte.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Um token de nome forte é a forma abreviada de uma chave pública usada para economizar espaço ao armazenar informações importantes nos metadados. Especificamente, os tokens de nome forte são usados em referências de assembly para referenciar o assembly dependente.  
  
 Se o `StrongNameTokenFromPublicKey` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [Método StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
