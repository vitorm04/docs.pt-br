---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f3c00f3a0efd41c425ba29f8465a73e78d624c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="f7a19-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="f7a19-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="f7a19-103">Cria outro enumerador de dispositivos de entrada raw com o mesmo estado do enumerador atual para iterar sobre a mesma lista.</span><span class="sxs-lookup"><span data-stu-id="f7a19-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7a19-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7a19-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7a19-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7a19-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="f7a19-106">[out] Endereço da variável de saída que recebe o [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="f7a19-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="f7a19-107">Se o método for bem-sucedida, o valor dessa variável de saída é indefinido.</span><span class="sxs-lookup"><span data-stu-id="f7a19-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f7a19-108">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f7a19-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="f7a19-109">HRESULT: Esse método oferece suporte a valores de retorno padrão E_INVALIDARG, E_OUTOFMEMORY e E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="f7a19-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7a19-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7a19-110">Remarks</span></span>  
 <span data-ttu-id="f7a19-111">Esse método torna possível registrar um ponto na sequência de enumeração para retornar ao ponto em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="f7a19-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="f7a19-112">O chamador deve liberar este novo enumerador separadamente do primeiro enumerador.</span><span class="sxs-lookup"><span data-stu-id="f7a19-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
