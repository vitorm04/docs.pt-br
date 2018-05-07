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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b736e58a1a48a2bb4492b6b8ff58af1567babcf5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>Método ICLRStrongName::StrongNameGetPublicKey
Obtém a chave pública de um par de chaves pública/privada. O par de chaves pode ser fornecido como um nome de contêiner de chave em um provedor de serviços de criptografia (CSP) ou como uma coleção bruta de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `szKeyContainer`  
 [in] O nome do recipiente de chave que contém o par de chaves pública/privada. Se `pbKeyBlob` for nulo, `szKeyContainer` deve especificar um contêiner válido dentro do CSP. Nesse caso, o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) método extrai a chave pública do par de chaves armazenado no contêiner.  
  
 Se `pbKeyBlob` não for null, o par de chaves é assumido para conter o objeto binário grande (BLOB) chave.  
  
 As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura. Não há outros tipos de chaves têm suporte no momento.  
  
 `pbKeyBlob`  
 [in] Um ponteiro para o par de chaves pública/privada. Esse par está no formato criado pelo Win32 `CryptExportKey` função. Se `pbKeyBlob` é null, o contêiner de chave especificado por `szKeyContainer` devem para conter o par de chaves.  
  
 `cbKeyBlob`  
 [in] O tamanho, em bytes, de `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] A chave pública retornada BLOB. O `ppbPublicKeyBlob` parâmetro é alocado pelo common language runtime e retornado ao chamador. O chamador deve liberar a memória usando o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.  
  
 `pcbPublicKeyBlob`  
 [out] O tamanho da chave pública retornado BLOB.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="remarks"></a>Comentários  
 A chave pública está contida em uma [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
