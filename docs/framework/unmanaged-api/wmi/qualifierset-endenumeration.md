---
title: Função QualifierSet_EndEnumeration (referência de API não gerenciada)
description: A função QualifierSet_EndEnumeration encerra uma enumeração.
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
ms.openlocfilehash: 0e24acdde486f377cc9187aac088ce7a611cd4eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460730"
---
# <a name="qualifiersetendenumeration-function"></a>Função QualifierSet_EndEnumeration
Finaliza a enumeração iniciada com uma chamada para o [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) função.  

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
[in] Um ponteiro para um [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instância.

## <a name="return-value"></a>Valor retornado

O seguinte valor retornado por essa função é definido no *WbemCli.h* arquivo de cabeçalho, ou você pode defini-la como uma constante em seu código:

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | A chamada de função foi bem-sucedida.  |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) método.

Esta chamada é recomendada, mas não é necessário. Imediatamente, ele libera recursos associados com a enumeração.

## <a name="requirements"></a>Requisitos  

**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
**Cabeçalho:** WMINet_Utils.idl  
  
**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também  
[WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
