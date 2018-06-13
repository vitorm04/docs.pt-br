---
title: Função ResetSecurity (referência de API não gerenciada)
description: A função ResetSecurity atribui um token de representação para o thread atual.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31e42b9e39ddb43025e18888572c394d742e38cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457900"
---
# <a name="resetsecurity-function"></a>Função ResetSecurity
Atribui o token de representação fornecido para o thread atual.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>Parâmetros

`token`  
[in] O token de representação para associar o thread atual. Seu valor pode ser `null`. 

## <a name="return-value"></a>Valor retornado

Se a função tiver êxito, o valor de retorno é `S_OK` (0).

Se a função falhar, o valor de retorno é um código de erro diferente de zero. Para obter mais informações sobre o erro, chame o [GetErrorInfo](geterrorinfo.md) função.
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
