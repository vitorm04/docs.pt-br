---
title: Função ResetSecurity (referência de API não gerenciada)
description: A função ResetSecurity atribui um token de representação ao thread atual.
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
ms.openlocfilehash: 95d91eac21e82e55af2f5e9ab181b770832f5ad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120204"
---
# <a name="resetsecurity-function"></a>Função ResetSecurity
Atribui o token de representação fornecido para o thread atual.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>Parâmetros

`token`  
no O token de representação a ser associado ao thread atual. Seu valor pode ser `null`. 

## <a name="return-value"></a>Valor retornado

Se a função for realizada com sucesso, o valor de retorno será `S_OK` (0).

Se a função falhar, o valor de retorno será um código de erro diferente de zero. Para obter informações de erro estendidas, chame a função [GetErrorInfo](geterrorinfo.md) .
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils. idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
