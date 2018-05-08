---
title: Método ICLRStrongName::StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b213285b3c533488cfa48198951275925c0e37ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a>Método ICLRStrongName::StrongNameKeyGenEx
Gera um novo par de chaves pública/privada com o tamanho de chave especificado para o uso de nome forte.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszKeyContainer`  
 [in] O nome do contêiner de chave solicitado. `wszKeyContainer` deve ser uma cadeia de caracteres não vazia ou null para gerar um nome temporário.  
  
 `dwFlags`  
 [in] Um valor que especifica se deve deixar a chave registrada. Há suporte para os seguintes valores:  
  
-   0x00000000 - usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporária.  
  
-   0x00000001 (`SN_LEAVE_KEY`)-Especifica que a chave deve ser registrada para a esquerda.  
  
 `dwKeySize`  
 [in] O tamanho solicitado da chave em bits.  
  
 `ppbKeyBlob`  
 [out] O par de chaves pública/privada retornado.  
  
 `pcbKeyBlob`  
 [out] O tamanho, em bytes, de `ppbKeyBlob`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="remarks"></a>Comentários  
 As versões do .NET Framework 1.0 e 1.1 exigem um `dwKeySize` de 1024 bits para assinar um assembly com um nome forte; a versão 2.0 adiciona suporte para chaves de 2048 bits.  
  
 Após a chave de recuperação, você deve chamar o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método para liberar a memória alocada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
