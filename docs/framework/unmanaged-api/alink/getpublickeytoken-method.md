---
title: Método GetPublicKeyToken
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 851ff82a539ce354d5507e829d8c461a0f2494ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729467"
---
# <a name="getpublickeytoken-method"></a>Método GetPublicKeyToken
Recupera o token de chave pública para um determinado arquivo de chave ou contêiner de chave.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszKeyFile`  
 Nome do arquivo da chave.  
  
 `pszKeyContainer`  
 Nome do contêiner de chave.  
  
 `pvPublicKeyToken`  
 Endereço no qual o token de chave deve ser armazenado.  
  
 `pcbPublicKeyToken`  
 Especifica o tamanho, em bytes, do buffer indicado pelo `pvPublicKeyToken`. Após o retorno, contém o número real de bytes usados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
