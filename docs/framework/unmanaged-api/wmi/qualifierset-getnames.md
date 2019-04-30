---
title: Função QualifierSet_GetNames (referência de API não gerenciada)
description: A função QualifierSet_GetNames recupera os nomes de qualificadores de um objeto ou propriedade.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da6321e50082c3f73477b8187cc5bf671655df21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943375"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames function

Recupera os nomes de todos os qualificadores ou de certas qualificadores que estão disponíveis no objeto atual ou à propriedade.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>Parâmetros

`vFunc`\
[in] Esse parâmetro é usado.

`ptr`\
[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.

`lFlags`\
[in] Um dos seguintes sinalizadores ou valores que especifica quais nomes a serem incluídos na enumeração.

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|  | 0 | Retorne os nomes de todos os qualificadores. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto. <br/> Para uma propriedade: Retorne apenas os qualificadores específicos para a propriedade (incluindo substituições) e não os qualificadores propagados da definição da classe. <br/> Para uma instância: Retorne apenas os nomes específicos da instância qualificador. <br/> Para uma classe: Retorne apenas qualificadores específicos à classe que está sendo derivada.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retornar apenas os nomes dos qualificadores propagados de outro objeto. <br/> Para uma propriedade: Retorno propagados apenas os qualificadores a essa propriedade de definição de classe e não os valores da propriedade em si. <br/> Para uma instância: Retorno apenas desses qualificadores propagados da definição da classe. <br/> Para uma classe: Retornar apenas os nomes de qualificador herdados de classes pai. |

`pstrNames`\
[out] Um novo `SAFEARRAY` que contém os nomes solicitados. A matriz pode ter 0 elementos. Se ocorrer um erro, um novo `SAFEARRAY` não será retornado.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para iniciar uma nova enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) método.

Depois de recuperar os nomes de qualificador, você pode acessar cada qualificador por nome, chamando o [QualifierSet_Get](qualifierset-get.md) função.

Não é um erro para um determinado objeto ter qualificadores de zero, portanto, o número de cadeias de caracteres em `pstrNames` após o retorno pode ser 0, mesmo que a função retorna `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** WMINet_Utils.idl

**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)