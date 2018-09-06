---
title: Função GetMethod (referência de API não gerenciada)
description: A função GetMethod recupera informações sobre um método.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a913de0ff20fba51295fd8282b58e3953be9bba2
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773953"
---
# <a name="getmethod-function"></a>Função GetMethod
Recupera informações sobre o método especifico.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`wszName`  
[in] O nome do método. Esse parâmetro não pode ser `null` e deve apontar para um válido `LPCWSTR`.

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`ppInSignature`   
[out] Um ponteiro para o endereço de um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve o paramteers em para o método de instância. Esse parâmetro será ignorado se ele for definido como `null`. 

`ppOutSignature`  
[out] Um ponteiro para o endereço de um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que descreve os parâmetros de saída para o método de instância. Esse parâmetro será ignorado se ele for definido como `null`. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não foi encontrada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) método.

Gerenciamento do Windows pode definir as [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ponteiro para `null` se o método não tem em parâmetros.

Na `ppInSignature` e `ppOutSignature` descrevem em parâmetros e out, respectivamente, como propriedades em um `IWbemClassObject` instância da classe system [parametry](/windows/desktop/WmiSdk/--parameters). As propriedades na `ppInsignature` são denominados **Param * * * n*, onde *n* é a posição do parâmetro na assinatura do método (como `Param1`, `Param2`, etc.). As propriedades na `ppOutSignature` também são nomeados **Param * * * n*, e o valor de retorno é denominado **ReturnValue**. Para obter mais informações e um exemplo, consulte [IWbemClassObject::GetMethod método](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Requisitos  
**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
