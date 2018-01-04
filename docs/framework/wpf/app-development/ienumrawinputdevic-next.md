---
title: IEnumRAWINPUTDEVIC:Next
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af6cb5bfe07923e13f1b76c785d830a9af15eaf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
