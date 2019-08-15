---
title: Função GetCurrentApartmentType (referência de API não gerenciada)
description: A função GetCurrentApartmentType recupera o tipo de apartamento no qual o chamador está sendo executado.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68eb4ba653098d847022da45e610cb4fa5496a8c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037960"
---
# <a name="getcurrentapartmenttype-function"></a>Função GetCurrentApartmentType
Recupera o tipo de apartment no qual o chamador está sendo executado.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a>Parâmetros

`vFunc`  
no Este parâmetro não é usado.

`ptr`  
no Um ponteiro para uma instância de [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .

`aptType`  
fora Um ponteiro para um valor de enumeração [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) que indica o apartamento do chamador.

## <a name="return-value"></a>Valor retornado

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `S_OK` | 0 | A função foi concluída com êxito. |
| `E_FAIL` | 0x80000008 | O chamador não está sendo executado em um apartamento. |
  
## <a name="remarks"></a>Comentários

Essa função encapsula uma chamada para o método [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .

## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [WMI e contadores de desempenho (referência de API não gerenciada)](index.md)
