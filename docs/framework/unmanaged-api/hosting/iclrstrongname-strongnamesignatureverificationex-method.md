---
title: Método ICLRStrongName::StrongNameSignatureVerificationEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b36e1d34b874f47f1edb0e1ffe3dc2fe2d87ddcc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787927"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a>Método ICLRStrongName::StrongNameSignatureVerificationEx
Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 [in] O caminho para o arquivo executável portátil (.exe ou. dll) para o assembly a ser verificado.  
  
 `fForceVerification`  
 [in] `true` para executar a verificação, mesmo se for necessário substituir as configurações do registro; caso contrário, `false`.  
  
 `pfWasVerified`  
 [out] `true` se a assinatura de nome forte foi verificado; caso contrário, `false`. `pfWasVerified` também é definido como `false` se a verificação for bem-sucedida devido a configurações de registro.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se a verificação for bem-sucedida; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="remarks"></a>Comentários  
 O [iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) método fornece uma funcionalidade semelhante para o [iclrstrongname:: Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) método. No entanto, o segundo parâmetro de entrada e o parâmetro de saída para [iclrstrongname:: Strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) são do tipo `BOOLEAN` em vez de `DWORD`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
