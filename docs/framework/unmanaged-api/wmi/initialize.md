---
title: Inicializar a função (referência de API não gerenciada)
description: A função Initialize executa a inicialização de WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8e87157a7adf45f35608aeba1067f2d66c8972
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081600"
---
# <a name="initialize-function"></a>Função Initialize
Executa a inicialização do WMI.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a>Parâmetros

`bAllowIManagementObjectQI`   
[in] `true` para indicar que as chamadas para QueryInterface em objetos WMI são permitidas; `false` caso contrário.

## <a name="return-value"></a>Valor retornado

A função sempre retorna `S_OK` (0).
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.def  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
