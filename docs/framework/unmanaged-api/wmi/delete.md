---
title: Excluir função (referência de API não gerenciada)
description: A função Delete exclui a propriedade especificada e todos os seus qualificadores de uma definição de classe do CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 791e75aa60fd651dde1555339e31664a3523e1eb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649127"
---
# <a name="delete-function"></a>Excluir função
Exclui a propriedade especificada e todos os seus qualificadores de uma definição de classe do CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.

`wszName`  
[in] O nome da propriedade a ser excluída. `wszName` deve ser um ponteiro para um válido `LPCWSTR`.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Ocorreu um erro não especificado. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | A propriedade não pode ser excluída. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszzName` é inválido. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não existe. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente para concluir a operação. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | A propriedade é herdada de uma classe base. |
| `WBEM_E_SYSTEM_PROPERTY` | | A propriedade é uma propriedade do sistema. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | A função excluída de um valor padrão de substituição para a classe atual. O valor padrão para essa propriedade na classe pai foi reactiviated. | 

## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) método.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
