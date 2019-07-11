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
ms.openlocfilehash: c1f838c26d45c0f3cfbd50ac0ce02d234b82ddae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746664"
---
# <a name="get-function"></a>Função Get

Recupera o valor da propriedade especificado se ele existir.

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
[in] Esse parâmetro é usado.

`ptr`\
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`wszName`\
[in] O nome da propriedade.

`lFlags`\
[in] Reservado. Esse parâmetro deve ser 0.

`pVal`\
[out] Se a função retornar com êxito, contém o valor da `wszName` propriedade. O `pval` argumento é atribuído o tipo correto e o valor do qualificador.

`pvtType`\
[out] Se a função retornar com êxito, contém um [constante de tipo CIM](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) que indica o tipo de propriedade. Seu valor também pode ser `null`. 

`plFlavor`\
[out] Se a função retornar com êxito, recebe informações sobre a origem da propriedade. Seu valor pode ser `null`, ou uma das seguintes constantes WBEM_FLAVOR_TYPE definidas na *WbemCli.h* arquivo de cabeçalho: 

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | A propriedade é uma propriedade de sistema padrão. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Para uma classe: A propriedade é herdada da classe pai. <br> Para uma instância: A propriedade, enquanto herdada da classe pai, não foi modificada pela instância.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Para uma classe: A propriedade pertence à classe derivada. <br> Para uma instância: A propriedade é modificada pela instância; ou seja, foi fornecido um valor ou um qualificador foi adicionado ou modificado. |

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não foi encontrada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) método.

O `Get` função também pode retornar propriedades do sistema.

O `pVal` argumento é atribuído o tipo correto e o valor para o qualificador e o COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) função

## <a name="requirements"></a>Requisitos

 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

 **Cabeçalho:** WMINet_Utils.idl

 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
