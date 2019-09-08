---
title: Função CertFreeAuthenticodeTimestamperInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8ecada29528b065ddad0abc80a850ee0f347f6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786999"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a>Função CertFreeAuthenticodeTimestamperInfo
Libera recursos alocados para a estrutura [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pTimestamperInfo`  
 [in, out] As informações do carimbo de data/hora que será liberado. Consulte a estrutura [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se a função for bem-sucedida. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também

- [Authenticode](index.md)
