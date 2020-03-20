---
title: Método ICLRStrongName::StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181930"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>Método ICLRStrongName::StrongNameGetPublicKey
Obtém a chave pública de um par de chaves públicas/privadas. O par de chaves pode ser fornecido como um nome de contêiner chave dentro de um provedor de serviços criptográficos (CSP) ou como uma coleção bruta de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szKeyContainer`  
 [em] O nome do recipiente de chave que contém o par de chaves público/privado. Se `pbKeyBlob` for `szKeyContainer` nulo, deve especificar um recipiente válido dentro do CSP. Neste caso, o método [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) extrai a chave pública do par de chaves armazenado no contêiner.  
  
 Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).  
  
 As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits. Nenhum outro tipo de chaves é suportado neste momento.  
  
 `pbKeyBlob`  
 [em] Um ponteiro para o par de tecla público/privado. Este par está no formato criado pela `CryptExportKey` função Win32. Se `pbKeyBlob` for nulo, o `szKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.  
  
 `cbKeyBlob`  
 [em] O tamanho, em bytes, de `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [fora] A chave pública devolvida BLOB. O `ppbPublicKeyBlob` parâmetro é alocado pelo tempo de execução do idioma comum e devolvido ao chamador. O chamador deve liberar a memória usando o método [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
 `pcbPublicKeyBlob`  
 [fora] O tamanho da chave pública devolvida BLOB.  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 A chave pública está contida em uma estrutura [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
