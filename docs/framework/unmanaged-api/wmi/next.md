---
title: Função Next (referência de API não gerenciada)
description: A função a próxima retireves a próxima propriedade em uma enumeração.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15d470ccf9384695aa38a50c2c062c1b660fea96
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43803022"
---
# <a name="next-function"></a>Função Next
Recupera a próxima propriedade em uma enumeração que começa com uma chamada para [BeginEnumeration](beginenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Next (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor     
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`lFlags`  
[in] Reservado. Esse parâmetro deve ser 0.

`pstrName`  
[out] Um novo `BSTR` que contém o nome da propriedade. Você pode definir esse parâmetro como `null` se o nome não for necessário.

`pVal`  
[out] Um `VARIANT` preenchido com o valor da propriedade. Você pode definir esse parâmetro como `null` se o valor não for necessário. Se a função retornar um código de erro, o `VARIANT` passado para `pVal` é esquerda sem modificações. 

`pvtType`  
[out] Um ponteiro para um `CIMTYPE` variável (um `LONG` no qual o tipo da propriedade é colocado). O valor dessa propriedade pode ser um `VT_NULL_VARIANT`, nesse caso, é necessário determinar o tipo real da propriedade. Esse parâmetro também pode ser `null`. 

`plFlavor`  
[out] `null`, ou um valor que recebe informações sobre a origem da propriedade. Consulte a seção [comentários] para os valores possíveis. 

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro é inválido. |
| `WBEM_E_UNEXPECTED` | 0x8004101d | Não houve nenhuma chamada para o [ `BeginEnumeration` ](beginenumeration.md) função. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para iniciar uma nova enumeração. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | O procedimento remoto chamar betweeen o processo atual e o gerenciamento do Windows falha. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Não há nenhum mais propriedades na enumeração. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) método.

Esse método também retorna as propriedades do sistema.

Se o tipo subjacente da propriedade é um caminho de objeto, uma data ou hora ou outro tipo especial, o tipo retornado não contém informações suficientes. O chamador deve examinar o `CIMTYPE` para a propriedade especificada determinar se a propriedade é uma referência de objeto, uma data ou hora ou outro tipo especial.

Se `plFlavor` não é `null`, o `LONG` valor recebe informações sobre a origem da propriedade, da seguinte maneira:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | A propriedade é uma propriedade de sistema padrão. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Para uma classe: A propriedade é herdada da classe pai. </br> Para uma instância: A propriedade, enquanto herdada da classe pai, não foi modificada pela instância.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Para uma classe: A propriedade pertence à classe derivada. </br> Para uma instância: A propriedade é modificada pela instância; ou seja, foi fornecido um valor ou um qualificador foi adicionado ou modificado. |

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
