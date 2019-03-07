---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485402"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="1d769-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="1d769-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="1d769-103">Cria outro enumerador de dispositivo brutos de entrada com o mesmo estado que o enumerador atual para iterar sobre a mesma lista.</span><span class="sxs-lookup"><span data-stu-id="1d769-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d769-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d769-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d769-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d769-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="1d769-106">[out] Endereço da variável de saída que recebe o [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) ponteiro de interface.</span><span class="sxs-lookup"><span data-stu-id="1d769-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="1d769-107">Se o método for bem-sucedido, o valor dessa variável de saída é indefinido.</span><span class="sxs-lookup"><span data-stu-id="1d769-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="1d769-108">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1d769-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="1d769-109">HRESULT: Esse método dá suporte aos valores retornados padrão E_INVALIDARG e E_OUTOFMEMORY E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="1d769-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d769-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d769-110">Remarks</span></span>  
 <span data-ttu-id="1d769-111">Esse método torna possível registrar um ponto na sequência de enumeração para retornar a esse ponto em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="1d769-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="1d769-112">O chamador deve liberar esse novo enumerador separadamente do primeiro enumerador.</span><span class="sxs-lookup"><span data-stu-id="1d769-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
