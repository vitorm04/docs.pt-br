---
title: Função CertFreeAuthenticodeSignerInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdb764417b757cd7388c49d7e5cac9a960074820
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142396"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>Função CertFreeAuthenticodeSignerInfo
Libera recursos alocados para o [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pSignerInfo`  
 [in, out] Informações de signatário a serem liberadas. Consulte a [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
