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
ms.openlocfilehash: 65b8cb74a028892a3494e818f2b523f75e8766a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460441"
---
# <a name="getmethod-function"></a>Função GetMethod
Recupera informações sobre o método especificado.

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
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`wszName`  
[in] O nome do método. Esse parâmetro não pode ser `null` e deve apontar para um válida `LPCWSTR`.

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`ppInSignature`   
[out] Um ponteiro para o endereço de um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) que descreve o paramteers em para o método de instância. Esse parâmetro é ignorado se for definido como `null`. 

`ppOutSignature`  
[out] Um ponteiro para o endereço de um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) que descreve os parâmetros de saída para o método de instância. Esse parâmetro é ignorado se for definido como `null`. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não foi encontrada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) método.

Gerenciamento do Windows pode definir o [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) ponteiro para `null` se o método não tem em parâmetros.

Em `ppInSignature` e `ppOutSignature` descrevem in e out parâmetros, respectivamente, como propriedades em um `IWbemClassObject` instância da classe system [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx). As propriedades na `ppInsignature` são denominados **Param * n*, onde *n* é a posição do parâmetro na assinatura de método (como `Param1`, `Param2`, etc.). As propriedades na `ppOutSignature` também são chamadas de **Param * n*, e o valor de retorno é denominado **ReturnValue**. Para obter mais informações e um exemplo, consulte [IWbemClassObject::GetMethod método](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).

## <a name="requirements"></a>Requisitos  
**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
