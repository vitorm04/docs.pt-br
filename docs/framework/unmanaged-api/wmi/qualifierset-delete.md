---
title: Função QualifierSet_Delete (referência de API não gerenciada)
description: A função QualifierSet_Delete exclui um qualificador por nome.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0e96ba458edfe7261fd5857b7bcb8486f4a6636
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="qualifiersetdelete-function"></a>Função QualifierSet_Delete
Exclui um qualificador especificado por nome.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`   
[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.

`wszName`   
[in] O nome do qualificador para excluir.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | O parâmetro `wszName` não é válido. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Excluir este qualificador é inválido. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | O qualificador especificado não foi encontrado. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | A substituição local foi excluída e o qualificador original do objeto pai retomou o escopo. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) método.

Devido a regras de propagação de qualificador, um qualificador específico foi herdado de outro objeto e simplesmente substituído na classe atual ou instância. Nesse caso, o `QualifierSet_Delete` método redefine o qualificador para seu valor original de herdadas. Nesse caso, a função retorna o código de status `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
