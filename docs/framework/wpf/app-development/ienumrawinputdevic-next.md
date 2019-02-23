---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: a1f76bf42da9a311633de39e42dee2055fac4a27
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745179"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Enumera os próximos `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) estruturas na lista do enumerador, retornando-a no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
  
 [in] Número de [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) estruturas retornadas no `rgelt`.  
  
 `rgelt`  
  
 [out] Matriz de tamanho celt (ou maior) para receber as estruturas RAWINPUTDEVICE enumeradas.  
  
 `pceltFetched`  
  
 [out] Ponteiro para o número de elementos realmente fornecidos em `rgelt`. Chamador pode passar `NULL` se `rgelt` é um.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: S_OK se o número de elementos fornecido é `celt`; S_FALSE caso contrário.
