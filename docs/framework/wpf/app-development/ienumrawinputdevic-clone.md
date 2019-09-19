---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053416"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="b727d-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="b727d-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="b727d-103">Cria outro enumerador de dispositivo de entrada bruto com o mesmo estado que o enumerador atual para iterar na mesma lista.</span><span class="sxs-lookup"><span data-stu-id="b727d-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b727d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b727d-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b727d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b727d-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="b727d-106">fora Endereço da variável de saída que recebe o ponteiro de interface [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) .</span><span class="sxs-lookup"><span data-stu-id="b727d-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="b727d-107">Se o método não for bem-sucedido, o valor dessa variável de saída será indefinido.</span><span class="sxs-lookup"><span data-stu-id="b727d-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b727d-108">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b727d-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="b727d-109">HRESULT: Esse método dá suporte aos valores de retorno padrão E_INVALIDARG, E_OUTOFMEMORY e E_UNEXPECTED.</span><span class="sxs-lookup"><span data-stu-id="b727d-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b727d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b727d-110">Remarks</span></span>  
 <span data-ttu-id="b727d-111">Esse método possibilita o registro de um ponto na sequência de enumeração para retornar a esse ponto em um momento posterior.</span><span class="sxs-lookup"><span data-stu-id="b727d-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="b727d-112">O chamador deve liberar esse novo enumerador separadamente do primeiro enumerador.</span><span class="sxs-lookup"><span data-stu-id="b727d-112">The caller must release this new enumerator separately from the first enumerator.</span></span>
