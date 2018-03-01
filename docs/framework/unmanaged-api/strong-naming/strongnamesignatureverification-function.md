---
title: "Função StrongNameSignatureVerification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0950efd6c5323aa6a0cd2f1455ac3226b21a2b92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignatureverification-function"></a>Função StrongNameSignatureVerification
Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.  
  
 Essa função foi preterida. Use o [Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 [in] O caminho para o executável (. dll ou .exe) arquivo portátil para o assembly verificar.  
  
 `dwInFlags`  
 [in] Sinalizadores para modificar o comportamento de verificação. Há suporte para os seguintes valores:  
  
-   `SN_INFLAG_FORCE_VER`(0x00000001) - força a verificação mesmo se for necessário substituir as configurações do registro.  
  
-   `SN_INFLAG_INSTALL`(0x00000002) - Especifica que esta é a primeira vez que o manifesto é verificado.  
  
-   `SN_INFLAG_ADMIN_ACCESS`(0x00000004) - Especifica que o cache permite acesso somente aos usuários que têm privilégios administrativos.  
  
-   `SN_INFLAG_USER_ACCESS`(0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.  
  
-   `SN_INFLAG_ALL_ACCESS`(0x00000010) - Especifica que o cache não fornecem nenhuma garantia de restrição de acesso.  
  
-   `SN_INFLAG_RUNTIME`(0x80000000) - reservado para a depuração.  
  
 `pdwOutFlags`  
 [out] Sinalizadores que indica se a assinatura de nome forte foi verificada. Há suporte para o seguinte valor:  
  
-   `SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - Este valor é definido como `false` para especificar se a verificação foi bem-sucedida devido às configurações do registro.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Se a verificação for bem-sucedida; Caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [Método StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
