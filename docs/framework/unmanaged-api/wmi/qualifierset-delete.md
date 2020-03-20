---
title: função QualifierSet_Delete (referência de API não gerenciada)
description: A função QualifierSet_Delete exclui um qualificador pelo nome.
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
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174895"
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

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`[em] Um ponteiro para uma instância [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)

`wszName`[em] O nome do qualificador para excluir.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | O parâmetro `wszName` não é válido. |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | Excluir este qualificador é ilegal. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | O qualificador especificado não foi encontrado. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem sucedida.  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | A substituição local foi excluída e o qualificador original do objeto pai retomou o escopo. |

## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IWbemQualifierSet::Delete.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)

Devido às regras de propagação do qualificador, um qualificador em particular pode ter sido herdado de outro objeto e meramente substituído na classe ou instância atual. Neste caso, `QualifierSet_Delete` o método redefine o qualificador ao seu valor herdado original. A função neste caso retorna `WBEM_S_RESET_TO_DEFAULT`o código de status .

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
