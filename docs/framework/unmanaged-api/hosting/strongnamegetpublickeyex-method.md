---
title: Método StrongNameGetPublicKeyEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176221"
---
# <a name="strongnamegetpublickeyex-method"></a>Método StrongNameGetPublicKeyEx
Obtém a chave pública de um par de chaves público/privado e especifica um algoritmo de hash e um algoritmo de assinatura.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pwzKeyContainer`  
 [em] O nome do recipiente de chave que contém o par de chaves público/privado. Se `pbKeyBlob` for `szKeyContainer` nulo, deve especificar um contêiner válido dentro do provedor de serviços criptográficos (CSP). Neste caso, `StrongNameGetPublicKeyEx` o método extrai a chave pública do par de chaves armazenado no recipiente.  
  
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
  
 `uHashAlgId`  
 [em] O algoritmo de hash da montagem. Consulte a seção Observações para obter uma lista de valores aceitos.  
  
 `uReserved`  
 [em] Reservado para uso futuro; padrões para nulo.  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 A chave pública está contida em uma estrutura [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir mostra o `uHashAlgId` conjunto de valores aceitos para o parâmetro.  
  
|Nome|Valor|  
|----------|-----------|  
|Nenhum|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [Método StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
