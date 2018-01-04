---
title: "Função SetSecurity (referência de API não gerenciada)"
description: "A função SetSecurity recupera o token de representação do thread atual."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb716d64bde9b298203e54d862ff4f1b2bcd170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="setsecurity-function"></a>Função SetSecurity
Recupera o token de representação associado ao segmento atual.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a>Parâmetros

`pNeedToReset`[out] Quando a função retornar, contém um ponteiro para um `boolean` que indica se o token deve ser redefinido chamando o [ResetSecurity](resetsecurity.md) função.  

`token`  
[out] Quando a função retornar, contém um ponteiro para o identificador de token de representação associado ao segmento atual. Seu valor pode ser `null` se não houver nenhum token associado ao segmento atual. 

## <a name="return-value"></a>Valor retornado

Se a função tiver êxito, o valor de retorno é `S_OK` (0).

Se a função falhar, o valor de retorno é um código de erro diferente de zero. Para obter mais informações sobre o erro, chame o [GetErrorInfo](geterrorinfo.md) função.
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
