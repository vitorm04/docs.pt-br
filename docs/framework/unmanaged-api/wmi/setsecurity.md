---
title: Função setsecurity (referência de API não gerenciada)
description: A função setsecurity recupera o token de representação do thread atual.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6d27779bcfc97e1c4156b8782896e83d4754491b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120219"
---
# <a name="setsecurity-function"></a>Função setsecurity

Recupera o token de representação associado ao thread atual. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a>Parâmetros

`pNeedToReset`\
fora Quando a função retorna, contém um ponteiro para um `boolean` que indica se o token deve ser redefinido chamando a função [ResetSecurity](resetsecurity.md) .

`token`\
fora Quando a função retorna, contém um ponteiro para o identificador do token de representação associado ao thread atual. Seu valor pode ser `null` se não houver nenhum token associado ao thread atual. 

## <a name="return-value"></a>Valor retornado

Se a função for realizada com sucesso, o valor de retorno será `S_OK` (0).

Se a função falhar, o valor de retorno será um código de erro diferente de zero. Para obter informações de erro estendidas, chame a função [GetErrorInfo](geterrorinfo.md) .

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Cabeçalho:** WMINet_Utils. idl

 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
