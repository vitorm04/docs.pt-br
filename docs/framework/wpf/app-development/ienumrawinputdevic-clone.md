---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: da089e5342e641ffebe22ca6a4a593f97faeb89c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545331"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="9a15d-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="9a15d-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="9a15d-103">Cria outro enumerador de dispositivos de entrada raw com o mesmo estado do enumerador atual para iterar sobre a mesma lista.</span><span class="sxs-lookup"><span data-stu-id="9a15d-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a15d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a15d-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a15d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a15d-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="9a15d-106">[out] Endereço da variável de saída que recebe o [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="9a15d-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="9a15d-107">Se o método for bem-sucedida, o valor dessa variável de saída é indefinido.</span><span class="sxs-lookup"><span data-stu-id="9a15d-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9a15d-108">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9a15d-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="9a15d-109">HRESULT: Esse método oferece suporte a valores de retorno padrão E_INVALIDARG, E_OUTOFMEMORY e E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="9a15d-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a15d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a15d-110">Remarks</span></span>  
 <span data-ttu-id="9a15d-111">Esse método torna possível registrar um ponto na sequência de enumeração para retornar ao ponto em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="9a15d-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="9a15d-112">O chamador deve liberar este novo enumerador separadamente do primeiro enumerador.</span><span class="sxs-lookup"><span data-stu-id="9a15d-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
