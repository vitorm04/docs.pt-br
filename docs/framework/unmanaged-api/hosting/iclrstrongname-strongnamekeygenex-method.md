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
ms.openlocfilehash: b09677a45c5d515aacb2cac709599140039a9dd8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899550"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a>Método ICLRStrongName::StrongNameKeyGenEx
Gera um novo par de chaves pública/privada com o tamanho de chave especificado, para uso de nome forte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszKeyContainer`  
 no O nome do contêiner de chave solicitado. `wszKeyContainer` deve ser uma cadeia de caracteres não vazia ou nula para gerar um nome temporário.  
  
 `dwFlags`  
 no Um valor que especifica se a chave deve ser desregistrada. Os valores a seguir têm suporte:  
  
- 0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.  
  
- 0x00000001 (`SN_LEAVE_KEY`) – especifica que a chave deve ser registrada.  
  
 `dwKeySize`  
 no O tamanho solicitado da chave, em bits.  
  
 `ppbKeyBlob`  
 fora O par de chaves pública/privada retornado.  
  
 `pcbKeyBlob`  
 fora O tamanho, em bytes, de `ppbKeyBlob`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="remarks"></a>Comentários  
 As versões 1,0 e 1,1 do .NET Framework exigem uma `dwKeySize` de 1024 bits para assinar um assembly com um nome forte; a versão 2,0 adiciona suporte para chaves de 2048 bits.  
  
 Depois que a chave for recuperada, você deverá chamar o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) para liberar a memória alocada.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
