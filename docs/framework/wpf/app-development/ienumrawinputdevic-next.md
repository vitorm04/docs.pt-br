---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: c7450a9ababa9cf3cb02d572f5ed84f0791d74e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053406"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Enumera as próximas `celt` estruturas [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) na lista do enumerador `rgelt` , retornando-as junto com o número real de elementos enumerados no. `pceltFetched`  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `celt`  
  
 no Número de estruturas [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) retornadas `rgelt`em.  
  
 `rgelt`  
  
 fora Matriz de tamanho celt (ou maior) para receber estruturas RAWINPUTDEVICE enumeradas.  
  
 `pceltFetched`  
  
 fora Ponteiro para o número de elementos realmente fornecidos no `rgelt`. O chamador pode passar `NULL` se `rgelt` for um.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: S_OK se o número de elementos fornecidos for `celt`; S_FALSE caso contrário.
