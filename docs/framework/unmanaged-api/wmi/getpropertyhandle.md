---
title: Função GetPropertyHandle (referência de API não gerenciada)
description: A função GetPropertyHandle retorna um identificador exclusivo que identifica uma propriedade.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d72b0da43971a74a08a249b19dfc0d446eeb5e6a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798547"
---
# <a name="getpropertyhandle-function"></a>Função GetPropertyHandle

Retorna um identificador exclusivo que reconhece uma propriedade.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
no Este parâmetro não é usado.

`ptr`\
no Um ponteiro para uma instância de [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`wszPropertyName`\
no Uma cadeia de caracteres com o caractere codificado por nulo que contém o nome da propriedade.

`pType`\
fora Um ponteiro para um [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) membro de enumeração que representa o tipo CIM da propriedade.

`pHandle`\
fora Um ponteiro para um inteiro que contém o identificador de propriedade.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | O nome de propriedade especificado não foi encontrado. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | A propriedade solicitada é do tipo `CIM_OBJECT` is `CIM_ARRAY`ou. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) .

Você pode usar esse identificador para identificar Propriedades ao usar métodos [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) para ler ou gravar valores de propriedade.

Os identificadores podem ser recuperados para propriedades de todos os `CIM_OBJECT` tipos `CIM_ARRAY`de dados diferentes de e. Os identificadores retornados funcionam em todas as instâncias de uma classe.

## <a name="requirements"></a>Requisitos

**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils.idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
