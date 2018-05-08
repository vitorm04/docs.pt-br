---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 3cf3231bd48290c5b6b0ce8eeb6534de564c0c85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
Enumera os próximos `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas na lista do enumerador, retornando-os no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
  
 [in] Número de [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas retornadas no `rgelt`.  
  
 `rgelt`  
  
 [out] Matriz de tamanho celt (ou maior) para receber as estruturas RAWINPUTDEVICE enumeradas.  
  
 `pceltFetched`  
  
 [out] Ponteiro para o número de elementos realmente fornecidos em `rgelt`. O chamador pode passar no `NULL` se `rgelt` é um.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: S_OK se o número de elementos fornecido é `celt`; S_FALSE caso contrário.
