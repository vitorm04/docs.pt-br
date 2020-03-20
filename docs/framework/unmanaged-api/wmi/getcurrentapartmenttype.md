---
title: Função GetCurrentApartmentType (referência a API não gerenciada)
description: A função GetCurrentApartmentType recupera o tipo de apartamento em que o chamador está executando.
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176819"
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

## <a name="parameters"></a>parâmetros

`vFunc`  
[em] Este parâmetro não é usado.

`ptr`  
[em] Um ponteiro para uma instância [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)

`aptType`  
[fora] Um ponteiro para um valor de enumeração [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) que indica o apartamento do chamador.

## <a name="return-value"></a>Valor retornado

|Constante  |Valor  |Descrição  |
|---------|---------|---------|
| `S_OK` | 0 | A função foi concluída com sucesso. |
| `E_FAIL` | 0x80000008 | O interlocutor não está executando em um apartamento. |
  
## <a name="remarks"></a>Comentários

Esta função envolve uma chamada para o método [IComThreadingInfo::GetCurrentApartmentType.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** WMINet_Utils.idl  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Confira também

- [WMI e Contadores de Desempenho (Referência de API Não Gerenciada)](index.md)
