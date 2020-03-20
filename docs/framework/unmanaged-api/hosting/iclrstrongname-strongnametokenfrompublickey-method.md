---
title: Método ICLRStrongName::StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176312"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>Método ICLRStrongName::StrongNameTokenFromPublicKey
Recebe um símbolo que representa uma chave pública. Um nome forte é a forma abreviada de uma chave pública.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pbPublicKeyBlob`  
 [em] Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usada para gerar a assinatura de nome forte.  
  
 `cbPublicKeyBlob`  
 [em] O tamanho, em bytes, de `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [fora] O token de nome forte `pbPublicKeyBlob`correspondente à chave passou em . O tempo de execução do idioma comum aloca a memória na qual o token retorna. O chamador deve liberar essa memória usando o método [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
 `pcbStrongNameToken`  
 [fora] O tamanho, em bytes, do nome forte devolvido token.  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 Um token de nome forte é a forma abreviada de uma chave pública que é usada para economizar espaço ao armazenar informações-chave em metadados. Especificamente, tokens de nome fortes são usados em referências de montagem para se referir ao conjunto dependente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
