---
title: "Função GetPropertyHandle (referência de API não gerenciada)"
description: "A função GetPropertyHandle retorna um identificador exclusivo que uma propriedade de identidades."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3af852fb4b9899a7937f288ffb65d8ca84e4aef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getpropertyhandle-function"></a>Função GetPropertyHandle
Retorna um identificador exclusivo que identifica uma propriedade.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instância.

`wszPropertyName`  
[in] Uma cadeia terminada em nulo de characaters UTF16 codificado que contém o nome da propriedade.   

`pType`  
[out] Um ponteiro para um [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) membro de enumeração que representa o tipo CIM da propriedade.

`pHandle`   
[out] Um ponteiro para um inteiro que contém o identificador de propriedade.

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | O nome da propriedade especificado não foi encontrado. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um parâmetro não é válido. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | A propriedade solicitada é do tipo são `CIM_OBJECT` ou `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) método.

Você pode usar esse identificador para identificar as propriedades ao usar [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) métodos para ler ou gravar valores de propriedade.

Identificadores podem ser recuperados para propriedades de todos os tipos de dados diferente de `CIM_OBJECT` e `CIM_ARRAY`. Retornado trabalho identificadores em todas as instâncias de uma classe.

## <a name="requirements"></a>Requisitos  
**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
