---
title: HerdafunçãoDa função (referência de API não gerenciada)
description: A função Herdade determina se uma classe ou instância deriva de uma classe pai específica.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174934"
---
# <a name="inheritsfrom-function"></a>Função InheritsFrom
Determina se a classe ou instância atual é derivada de uma classe pai especificada.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszAncestor`  
[em] O nome da classe. `wszAncestor`deve apontar para `LPCWSTR`um válido .

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | O objeto atual `wszAncestor`herda de .  |
| `WBEM_S_FALSE` | 1 | O objeto atual não `wszAncestor`herda de . |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` é `null`. |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o [método IWbemClassObject::InheritsFrom.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom)

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
