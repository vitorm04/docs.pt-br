---
title: Função QualifierSet_EndEnumeration (referência de API não gerenciada)
description: A função de QualifierSet_EndEnumeration encerra uma enumeração.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbf47dbfddac7d48b78c9d52969de1ef03385c15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524308"
---
# <a name="qualifiersetendenumeration-function"></a>Função QualifierSet_EndEnumeration
Finaliza a enumeração começada com uma chamada para o [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) função.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
[in] Esse parâmetro é usado.

`ptr`   
[in] Um ponteiro para um [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instância.

## <a name="return-value"></a>Valor retornado

O seguinte valor retornado por essa função é definido na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-la como uma constante em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) método.

Essa chamada é recomendada, mas não é necessário. Ele libera imediatamente os recursos associados com a enumeração.

## <a name="requirements"></a>Requisitos  

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
**Cabeçalho:** WMINet_Utils.idl  
  
**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
