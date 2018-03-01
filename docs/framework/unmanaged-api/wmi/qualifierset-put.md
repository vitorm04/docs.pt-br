---
title: "Função QualifierSet_Put (referência de API não gerenciada)"
description: "A função QualifierSet_Put grava o qualificador nomeado e seu valor."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1bf5c6dbf0f707942d58f4d7cf155636f0532724
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetput-function"></a>Função QualifierSet_Put
Grava o qualificador de nome e o valor. O novo qualificador substitui o valor anterior do mesmo nome. Se o qualificador não existir, ele será criado. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QualifierSet_Put (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`   
[in] Esse parâmetro é usado.

`ptr`   
[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.

`wszName`   
[in] O nome do qualificador de gravar.

`pVal`[in] Um ponteiro para um válida `VARIANT` que contém o qualificador para gravação. O parâmetro não pode ser `null`.

`lFlavor`[in] Uma das seguintes constantes que define os tipos de qualificadores desejado para este qualificador. O valor padrão é `WBEM_FLAVOR_OVERRIDABLE` (0).

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | O qualificador pode ser substituído em uma classe derivada ou instância. **Este é o valor padrão.** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | O qualificador é propagado para instâncias. |
| `WBEM_FLAVOR_GLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | O qualificador é propagado para classes derivadas. |
| ' WBEM_FLAVOR_NOT_OVERRIDABLE | 0x10 | O qualificador não pode ser substituído em uma classe derivada ou instância. |
| ' WBEM_FLAVOR_AMENDED | 0x80 | O qualificador é localizado. |

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | Houve uma tentativa ilegal de especificar o **chave** qualificador em uma propriedade que não pode ser uma chave. As chaves são especificadas om o c; definição ass de um objeto e não pode ser alterada em uma base por instância. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | O `pVal` parâmetro não é de um tipo de Qualificador legal. |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | Não é possível chamar o `QualifierSet_Put` método o qualificador porque o objeto proprietário não permite substituições. |
| `WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::Put](https://msdn.microsoft.com/library/aa391871(v=vs.85).aspx) método.

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
