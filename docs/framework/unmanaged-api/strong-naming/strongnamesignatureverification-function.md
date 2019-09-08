---
title: Função StrongNameSignatureVerification
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8943df861b1bff2b28c68d0233fc336d1b5d4579
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798941"
---
# <a name="strongnamesignatureverification-function"></a>Função StrongNameSignatureVerification
Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 no O caminho para o arquivo executável portátil (. dll ou. exe) para o assembly verificar.  
  
 `dwInFlags`  
 no Sinalizadores para modificar o comportamento de verificação. Há suporte para os seguintes valores:  
  
- `SN_INFLAG_FORCE_VER`(0x00000001) – força a verificação mesmo que seja necessário substituir as configurações do registro.  
  
- `SN_INFLAG_INSTALL`(0x00000002) – especifica que esta é a primeira vez que o manifesto é verificado.  
  
- `SN_INFLAG_ADMIN_ACCESS`(0x00000004) – especifica que o cache permitirá acesso somente aos usuários que têm privilégios administrativos.  
  
- `SN_INFLAG_USER_ACCESS`(0x00000008) – especifica que o assembly será acessível somente para o usuário atual.  
  
- `SN_INFLAG_ALL_ACCESS`(0x00000010) – especifica que o cache não oferecerá nenhuma garantia de restrição de acesso.  
  
- `SN_INFLAG_RUNTIME`(0x80000000)-reservado para depuração interna.  
  
 `pdwOutFlags`  
 fora Sinalizadores que indicam se a assinatura de nome forte foi verificada. Há suporte para o seguinte valor:  
  
- `SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-esse valor é definido como `false` para especificar que a verificação foi bem-sucedida devido a configurações do registro.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`se a verificação foi bem-sucedida; caso contrário `false`,.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [Método StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
