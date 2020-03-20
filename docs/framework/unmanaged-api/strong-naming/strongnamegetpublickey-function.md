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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176923"
---
# <a name="strongnamegetpublickey-function"></a>Função StrongNameGetPublicKey
Obtém a chave pública de um par de chaves pública/privada. O par de chaves pode ser fornecido como um nome de contêiner chave dentro de um provedor de serviços criptográficos (CSP) ou como uma coleção bruta de bytes.  
  
 Esta função foi preterida. Use o método [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szKeyContainer`  
 [em] O nome do recipiente de chave que contém o par de chaves público/privado. Se `pbKeyBlob` for `szKeyContainer` nulo, deve especificar um recipiente válido dentro do CSP. Neste caso, `StrongNameGetPublicKey` extrai a chave pública do par de chaves armazenado no recipiente.  
  
 Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).  
  
 As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits. Nenhum outro tipo de chaves é suportado neste momento.  
  
 `pbKeyBlob`  
 [em] Um ponteiro para o par de tecla público/privado. Este par está no formato criado pela `CryptExportKey` função Win32. Se `pbKeyBlob` for nulo, o `szKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.  
  
 `cbKeyBlob`  
 [em] O tamanho, em bytes, de `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [fora] A chave pública devolvida BLOB. O `ppbPublicKeyBlob` parâmetro é alocado pelo tempo de execução do idioma comum e devolvido ao chamador. O chamador deve liberar a memória usando a função [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbPublicKeyBlob`  
 [fora] O tamanho da chave pública devolvida BLOB.  
  
## <a name="return-value"></a>Valor retornado  
 `true`em conclusão bem sucedida; caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 A chave pública está contida em uma estrutura [PublicKeyBlob.](publickeyblob-structure.md)  
  
 Se `StrongNameGetPublicKey` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [Método StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
- [Estrutura PublicKeyBlob](publickeyblob-structure.md)
