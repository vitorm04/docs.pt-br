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
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="4288c-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="4288c-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="4288c-103">Enumera os próximos `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas na lista do enumerador, retornando-os no `rgelt` juntamente com o número real de elementos enumerados em `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="4288c-103">Enumerates the next `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4288c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4288c-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4288c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4288c-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="4288c-106">[in] Número de [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) estruturas retornadas no `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="4288c-106">[in] Number of [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="4288c-107">[out] Matriz de tamanho celt (ou maior) para receber as estruturas RAWINPUTDEVICE enumeradas.</span><span class="sxs-lookup"><span data-stu-id="4288c-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="4288c-108">[out] Ponteiro para o número de elementos realmente fornecidos em `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="4288c-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="4288c-109">O chamador pode passar no `NULL` se `rgelt` é um.</span><span class="sxs-lookup"><span data-stu-id="4288c-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4288c-110">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4288c-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="4288c-111">HRESULT: S_OK se o número de elementos fornecido é `celt`; S_FALSE caso contrário.</span><span class="sxs-lookup"><span data-stu-id="4288c-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
