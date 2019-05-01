---
title: Função StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e38a85b688d66e9f44bd8026bb4c9e141a6eb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000331"
---
# <a name="strongnamegetpublickey-function"></a>Função StrongNameGetPublicKey
Obtém a chave pública de um par de chaves pública/privada. O par de chaves pode ser fornecido como um nome de contêiner de chave dentro de um provedor de serviços de criptografia (CSP) ou como uma coleção bruta de bytes.  
  
 Essa função foi preterida. Use o [iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szKeyContainer`  
 [in] O nome do contêiner de chave que contém o par de chaves pública/privada. Se `pbKeyBlob` for nulo, `szKeyContainer` deve especificar um contêiner válido dentro do CSP. Nesse caso, `StrongNameGetPublicKey` extrai a chave pública do par de chaves armazenado no contêiner.  
  
 Se `pbKeyBlob` não for nulo, presume-se o par de chaves para caber no objeto binário grande (BLOB) chave.  
  
 As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura. Não há outros tipos de chaves têm suporte no momento.  
  
 `pbKeyBlob`  
 [in] Um ponteiro para o par de chaves pública/privada. Esse par está no formato criado pelo Win32 `CryptExportKey` função. Se `pbKeyBlob` for nula, o contêiner de chave especificado por `szKeyContainer` deve para conter o par de chaves.  
  
 `cbKeyBlob`  
 [in] O tamanho, em bytes, do `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [out] A chave pública retornada BLOB. O `ppbPublicKeyBlob` parâmetro é alocado pelo common language runtime e retornado ao chamador. O chamador deve liberar a memória usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.  
  
 `pcbPublicKeyBlob`  
 [out] O tamanho da chave pública retornado BLOB.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 A chave pública está contida em uma [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) estrutura.  
  
 Se o `StrongNameGetPublicKey` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [Método StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [Estrutura PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
