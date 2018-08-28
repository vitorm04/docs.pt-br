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
ms.openlocfilehash: 84059c5e5542e13b1d4fc4efcfc4c7f418db391e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999372"
---
# <a name="qualifiersetgetnames-function"></a>Função QualifierSet_GetNames
Recupera os nomes de todos os qualificadores ou de certas qualificadores que estão disponíveis no objeto atual ou à propriedade. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`   
[in] Esse parâmetro é usado.

`ptr`   
[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.

`lFlags`   
[in] Um dos seguintes sinalizadores ou valores que especifica quais nomes a serem incluídos na enumeração.

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|  | 0 | Retorne os nomes de todos os qualificadores. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto. <br/> Para uma propriedade: retornar apenas os qualificadores específica para a propriedade (incluindo substituições), e não os qualificadores propagadas da definição da classe. <br/> Para uma instância: retornar apenas os nomes de qualificador de específico da instância. <br/> Para uma classe: retornar apenas os qualificadores específica para o beiong de classe derivada.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retornar apenas os nomes dos qualificadores propagados de outro objeto. <br/> Para uma propriedade: retorno propagados apenas os qualificadores a essa propriedade de definição de classe e não os valores da propriedade em si. <br/> Para uma instância: retorno apenas desses qualificadores propagados da definição da classe. <br/> Para uma classe: retornar apenas os nomes de qualificador herdados de classes pai. |

`pstrNames` [out] Um novo `SAFEARRAY` que contém os nomes solicitados. A matriz pode ter 0 elementos. Se ocorrer um erro, um novo `SAFEARRAY` não será retornado.

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
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
