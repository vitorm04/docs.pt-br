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
ms.openlocfilehash: b7c96439cf50c18e336baa70cf463b9463203290
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461172"
---
# <a name="qualifiersetgetnames-function"></a>Função QualifierSet_GetNames
Recupera os nomes de todos os qualificadores ou de certos qualificadores disponíveis do objeto atual ou propriedade. 

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
[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.

`lFlags`   
[in] Um dos seguintes sinalizadores ou valores que especifica os nomes a serem incluídos na enumeração.

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|  | 0 | Retorne os nomes de todos os qualificadores. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Retorne apenas os nomes dos qualificadores específica para a propriedade atual ou o objeto. <br/> Para uma propriedade: retornar apenas os qualificadores específica para a propriedade (incluindo substituições), e não os qualificadores propagadas da definição de classe. <br/> Para uma instância: retornar apenas os nomes de qualificador específicos da instância. <br/> Para uma classe: retornar somente qualificadores específico para o beiong de classe derivada.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Retornar apenas os nomes dos qualificadores propagados de outro objeto. <br/> Para uma propriedade: retorno apenas os qualificadores propagados para essa propriedade de definição de classe e não os da própria propriedade. <br/> Para uma instância: retornar apenas os qualificadores propagados da definição de classe. <br/> Para uma classe: retornar apenas os nomes de qualificador herdados de classes pai. |

`pstrNames` [out] Um novo `SAFEARRAY` que contém os nomes solicitados. A matriz pode ter elementos 0. Se ocorrer um erro, um novo `SAFEARRAY` não é retornado.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para iniciar uma nova enumeração. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::GetNames](https://msdn.microsoft.com/library/aa391868(v=vs.85).aspx) método.

Depois de recuperar os nomes de qualificador, você pode acessar cada qualificador por nome, chamando o [QualifierSet_Get](qualifierset-get.md) função. 

Não é um erro para um determinado objeto ter qualificadores de zero, então o número de cadeias de caracteres em `pstrNames` no retorno pode ser 0, mesmo que a função retornará `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
