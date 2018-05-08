---
title: Função GetHashFromBlob
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 427d93a9aff527d36720c4199782fa104a66f8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="gethashfromblob-function"></a>Função GetHashFromBlob
Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.  
  
 Essa função foi preterida. Use o [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbBlob`  
 [in] Um ponteiro para o endereço do bloco de memória a ser transformado em hash.  
  
 `cchBlob`  
 [in] O comprimento, em bytes, do bloco de memória.  
  
 `piHashAlg`  
 [out no] Uma constante que especifica o algoritmo de hash. Use zero para o algoritmo padrão.  
  
 `pbHash`  
 [out] O buffer de hash retornado.  
  
 `cchHash`  
 [in] O tamanho máximo solicitado da `pbHash`.  
  
 `pchHash`  
 [out] O tamanho, em bytes, do retornado `pbHash`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
