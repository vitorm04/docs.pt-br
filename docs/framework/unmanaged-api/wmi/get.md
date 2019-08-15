---
title: Obter função (referência de API não gerenciada)
description: A função Get recupera o valor da propriedade especificada.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 265d3edbd3175eebcf6fd35be24f5b66144c960f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037949"
---
# <a name="get-function"></a>Função Get

Recupera o valor da propriedade especificada, se existir.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
no O nome da propriedade.

`lFlags`\
[in] Reservado. Esse parâmetro deve ser 0.

`pVal`\
fora Se a função retornar com êxito, conterá o valor da `wszName` propriedade. O `pval` argumento recebe o tipo e o valor corretos para o qualificador.

`pvtType`\
fora Se a função retornar com êxito, conterá uma [constante do tipo CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) que indica o tipo de propriedade. Seu valor também pode ser `null`. 

`plFlavor`\
fora Se a função retornar com êxito, o receberá informações sobre a origem da propriedade. Seu valor pode ser `null`ou uma das seguintes constantes WBEM_FLAVOR_TYPE definidas no arquivo de cabeçalho *WbemCli. h* : 

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | A propriedade é uma propriedade padrão do sistema. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Para uma classe: A propriedade é herdada da classe pai. <br> Para uma instância: A propriedade, embora herdada da classe pai, não foi modificada pela instância.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Para uma classe: A propriedade pertence à classe derivada. <br> Para uma instância: A propriedade é modificada pela instância; ou seja, um valor foi fornecido ou um qualificador foi adicionado ou modificado. |

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não foi encontrada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .

A `Get` função também pode retornar propriedades do sistema.

O argumento recebe o tipo e o valor corretos para o qualificador e a função [VariantInit com](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) `pVal`

## <a name="requirements"></a>Requisitos

 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

 **Cabeçalho:** WMINet_Utils.idl

 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
