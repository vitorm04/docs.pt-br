---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: a74f71345a22f6d766c2d5966ca5d2cb33ab756e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053372"
---
# <a name="ienumrawinputdevicskip"></a>IEnumRAWINPUTDEVIC:Skip
Instrui o enumerador a ignorar os próximos `celt` elementos na enumeração para que a próxima chamada para [IEnumRAWINPUTDEVIC: Next](ienumrawinputdevic-next.md) não retorne esses elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `celt`  
  
 no Número de elementos a serem ignorados.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: S_OK se o número de elementos fornecidos for `celt`; S_FALSE caso contrário.
