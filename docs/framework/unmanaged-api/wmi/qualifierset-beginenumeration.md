---
title: Função QualifierSet_BeginEnumeration (referência de API não gerenciada)
description: A função QualifierSet_BeginEnumeration redefine um enumerador os qualificadores de um objeto.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d20701237501834c611c4e498c39597cf275176
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407028"
---
# <a name="qualifiersetbeginenumeration-function"></a>Função QualifierSet_BeginEnumeration
Redefine um enumerador os qualificadores de um objeto para o início da enumeração.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`   
[in] Esse parâmetro é usado.

`ptr`   
[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.

`lFlags`   
[in] Uma combinação bit a bit de sinalizadores ou valores descritos na [comentários](#remarks) seção que especifica os qualificadores a serem incluídos na enumeração.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | O parâmetro `lFlags` não é válido. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Uma segunda chamada para `QualifierSet_BeginEnumeration` foi feita sem uma chamada intermediária para [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para iniciar uma nova enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) método.

Para enumerar todos os qualificadores em um objeto, esse método deve ser chamado antes da primeira chamada para [QualifierSet_Next](qualifierset-next.md). A ordem na qual os qualificadores são enumerados é garantida para ser invariável para uma enumeração de determinado.

Os sinalizadores que podem ser passados como o `lEnumFlags` argumento são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código.   

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|  | 0 | Retorne os nomes de todos os qualificadores. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto. <br/> Para uma propriedade: retornar apenas os qualificadores específica para a propriedade (incluindo substituições), e não os qualificadores propagadas da definição da classe. <br/> Para uma instância: retornar apenas os nomes de qualificador de específico da instância. <br/> Para uma classe: retornar apenas os qualificadores específica para o beiong de classe derivada.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retornar apenas os nomes dos qualificadores propagados de outro objeto. <br/> Para uma propriedade: retorno propagados apenas os qualificadores a essa propriedade de definição de classe e não os valores da propriedade em si. <br/> Para uma instância: retorno apenas desses qualificadores propagados da definição da classe. <br/> Para uma classe: retornar apenas os nomes de qualificador herdados de classes pai. |

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
