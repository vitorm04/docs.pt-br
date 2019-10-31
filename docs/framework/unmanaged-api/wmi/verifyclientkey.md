---
title: Função VerifyClientKey (referência de API não gerenciada)
description: A função VerifyClientKey garante que a chave do cliente tenha a segurança correta.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a0680651eb192e2798ede00048599c5130e63f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107358"
---
# <a name="verifyclientkey-function"></a>Função VerifyClientKey
Garante que a chave do cliente tenha a segurança correta.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Valor retornado

Se a função for realizada com sucesso, o valor de retorno será `ERROR_SUCCESS` (0).

Se a função falhar, o valor de retorno será um código de erro diferente de zero definido em *Winerror. h*.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils. def  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
