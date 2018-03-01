---
title: "Obter função (referência de API não gerenciada)"
description: "A função Get recupera o valor da propriedade especificada."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69312030689ab1b87e3aadd040395f06e1c94ac8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="get-function"></a>Função Get
Recupera o valor da propriedade especificado se ele existir.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`  
[in] Um ponteiro para um [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instância.

`wszName`  
[in] O nome da propriedade.

`lFlags`[in] Reservado. Esse parâmetro deve ser 0.

`pVal`[out] Se a função retornar com êxito, contém o valor de `wszName` propriedade. O `pval` argumento recebe o tipo correto e o valor do qualificador.

`pvtType`[out] Se a função retornar com êxito, contém um [constante do tipo CIM](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) que indica o tipo de propriedade. O valor também pode ser `null`. 

`plFlavor`[out] Se a função retornar com êxito, recebe informações sobre a origem da propriedade. Seu valor pode ser `null`, ou uma das seguintes constantes WBEM_FLAVOR_TYPE definidas no *WbemCli.h* arquivo de cabeçalho: 

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | A propriedade é uma propriedade de sistema padrão. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Para uma classe: A propriedade é herdada da classe pai. </br> Para uma instância: A propriedade, enquanto herdada da classe pai, não foi modificada pela instância.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Para uma classe: A propriedade pertence à classe derivada. </br> Para uma instância: A propriedade é modificada pela instância; ou seja, foi fornecido um valor ou um qualificador foi adicionado ou modificado. |

## <a name="return-value"></a>Valor retornado

Os seguintes valores retornados por essa função são definidos no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Houve uma falha geral. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Um ou mais parâmetros não são válidos. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | A propriedade especificada não foi encontrada. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Não há memória suficiente está disponível para concluir a operação. |
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemClassObject::Get](https://msdn.microsoft.com/library/aa391442(v=vs.85).aspx) método.

O `Get` função também pode retornar propriedades do sistema.

O `pVal` argumento recebe o tipo correto e o valor para o qualificador e o COM [VariantInit](https://msdn.microsoft.com/library/ms221402(v=vs.85).aspx) função

## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
