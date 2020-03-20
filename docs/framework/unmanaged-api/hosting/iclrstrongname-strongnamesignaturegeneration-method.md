---
title: Método ICLRStrongName::StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178046"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>Método ICLRStrongName::StrongNameSignatureGeneration
Gera uma assinatura de nome forte para o assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `wszFilePath`  
 [em] O caminho para o arquivo que contém o manifesto da montagem para o qual a assinatura de nome forte será gerada.  
  
 `wszKeyContainer`  
 [em] O nome do recipiente de chave que contém o par de chaves público/privado.  
  
 Se `pbKeyBlob` for `wszKeyContainer` nulo, deve especificar um contêiner válido dentro do provedor de serviços criptográficos (CSP). Neste caso, o par de chaves armazenado no recipiente é usado para assinar o arquivo.  
  
 Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).  
  
 As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits. Nenhum outro tipo de chaves é suportado neste momento.  
  
 `pbKeyBlob`  
 [em] Um ponteiro para o par de tecla público/privado. Este par está no formato criado pela `CryptExportKey` função Win32. Se `pbKeyBlob` for nulo, o `wszKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.  
  
 `cbKeyBlob`  
 [em] O tamanho, em bytes, de `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [fora] Um ponteiro para o local para o qual o tempo de execução do idioma comum retorna a assinatura. Se `ppbSignatureBlob` for nulo, o tempo de execução `wszFilePath`armazena a assinatura no arquivo especificado por .  
  
 Se `ppbSignatureBlob` não for nulo, o tempo de execução do idioma comum aloca espaço para retornar a assinatura. O chamador deve liberar este espaço usando o método [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
  
 `pcbSignatureBlob`  
 [fora] O tamanho, em bytes, da assinatura retornada.  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 Especifique nulo `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.  
  
 A assinatura pode ser armazenada diretamente no arquivo ou devolvida ao chamador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
