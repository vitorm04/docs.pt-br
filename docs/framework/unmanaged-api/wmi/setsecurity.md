---
title: Função SetSecurity (referência de API não gerenciada)
description: A função SetSecurity recupera o token de personificação do segmento atual.
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
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176728"
---
# <a name="setsecurity-function"></a>Função SetSecurity

Recupera o token de representação associado ao thread atual.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a>parâmetros

`pNeedToReset`\
[fora] Quando a função retorna, contém `boolean` um ponteiro para um que indica se o token deve ser redefinido chamando a função [ResetSecurity.](resetsecurity.md)

`token`\
[fora] Quando a função retorna, contém um ponteiro para a alça do token de representação associado ao segmento atual. Seu valor `null` pode ser se não houver nenhum token associado ao segmento atual.

## <a name="return-value"></a>Valor retornado

Se a função for bem `S_OK` sucedida, o valor de retorno será (0).

Se a função falhar, o valor de retorno será um código de erro não-zero. Para obter informações de erro estendidas, ligue para a função [GetErrorInfo.](geterrorinfo.md)

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Cabeçalho:** WMINet_Utils.idl

 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
