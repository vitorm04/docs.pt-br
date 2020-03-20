---
title: Obter função (referência de API não gerenciada)
description: A função Obter recupera o valor de propriedade especificado.
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
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174973"
---
# <a name="get-function"></a>Função Get

Recupera o valor de propriedade especificado se ele existir.

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

## <a name="parameters"></a>parâmetros

`vFunc`\
[em] Este parâmetro não é usado.

`ptr`\
[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)

`wszName`\
[em] O nome da propriedade.

`lFlags`\
[in] Reservado. Este parâmetro deve ser 0.

`pVal`\
[fora] Se a função retornar com sucesso, contém o valor da `wszName` propriedade. O `pval` argumento é atribuído ao tipo e valor corretos para o qualificador.

`pvtType`\
[fora] Se a função retornar com sucesso, contém uma [constante do tipo CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) que indica o tipo de propriedade. Seu valor também `null`pode ser .

`plFlavor`\
[fora] Se a função retornar com sucesso, recebe informações sobre a origem da propriedade. Seu valor `null`pode ser , ou uma das seguintes WBEM_FLAVOR_TYPE constantes definidas no arquivo de cabeçalho *WbemCli.h:*

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | A propriedade é uma propriedade padrão do sistema. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Para uma classe: A propriedade é herdada da classe dos pais. <br> Por exemplo: a propriedade, embora herdada da classe pai, não foi modificada pela instância.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Para uma classe: A propriedade pertence à classe derivada. <br> Por exemplo: A propriedade é modificada pela instância; ou seja, um valor foi fornecido, ou um qualificador foi adicionado ou modificado. |

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve um fracasso geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não foi encontrada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória disponível suficiente para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |

## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemClassObject::Get.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)

A `Get` função também pode retornar as propriedades do sistema.

O `pVal` argumento é atribuído ao tipo e valor corretos para o qualificador e a função COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)

## <a name="requirements"></a>Requisitos

 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).

 **Cabeçalho:** WMINet_Utils.idl

 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
