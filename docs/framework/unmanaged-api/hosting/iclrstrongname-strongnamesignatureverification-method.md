---
title: Método ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49041031742332fbc275a9dbde91e640eb428c28
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785876"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a>Método ICLRStrongName::StrongNameSignatureVerification
Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 [in] O caminho para o arquivo executável portátil (. dll ou .exe) para o assembly verificar.  
  
 `dwInFlags`  
 [in] Sinalizadores para modificar o comportamento de verificação. Há suporte para os seguintes valores:  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - força a verificação, mesmo se for necessário substituir as configurações do registro.  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - Especifica que esta é a primeira vez que o manifesto é verificado.  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Especifica que o cache permitirá o acesso somente aos usuários que têm privilégios administrativos.  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) - Especifica que o cache não será fornecer nenhuma garantia de restrição de acesso.  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - reservado para a depuração.  
  
 `pdwOutFlags`  
 [out] Sinalizadores que indica se a assinatura de nome forte foi verificada. Há suporte para o seguinte valor:  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - esse valor é definido como `false` para especificar que a verificação for bem-sucedida devido a configurações de registro.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
