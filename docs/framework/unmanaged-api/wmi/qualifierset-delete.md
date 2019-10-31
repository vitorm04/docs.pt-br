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
ms.openlocfilehash: e7bedcb5c56f9976f8dfd2619081971075d0d809
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127294"
---
# <a name="qualifierset_delete-function"></a>Função QualifierSet_Delete
Exclui um qualificador especificado por nome.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
no Este parâmetro não é usado.

`ptr`   
no Um ponteiro para uma instância de [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`   
no O nome do qualificador a ser excluído.

## <a name="return-value"></a>Valor retornado

Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | O parâmetro `wszName` não é válido. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | A exclusão deste qualificador é inválida. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | O qualificador especificado não foi encontrado. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | A substituição local foi excluída e o qualificador original do objeto pai retomou o escopo. |

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IWbemQualifierSet::D xcluir](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .

Devido a regras de propagação de qualificador, um qualificador específico pode ter sido herdado de outro objeto e meramente substituído na classe ou instância atual. Nesse caso, o método `QualifierSet_Delete` redefine o qualificador para seu valor herdado original. Nesse caso, a função retorna o código de status `WBEM_S_RESET_TO_DEFAULT`.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils. idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
