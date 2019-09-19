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
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Cria outro enumerador de dispositivo de entrada bruto com o mesmo estado que o enumerador atual para iterar na mesma lista.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppenum`  
  
 fora Endereço da variável de saída que recebe o ponteiro de interface [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) . Se o método não for bem-sucedido, o valor dessa variável de saída será indefinido.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: Esse método dá suporte aos valores de retorno padrão E_INVALIDARG, E_OUTOFMEMORY e E_UNEXPECTED.  
  
## <a name="remarks"></a>Comentários  
 Esse método possibilita o registro de um ponto na sequência de enumeração para retornar a esse ponto em um momento posterior. O chamador deve liberar esse novo enumerador separadamente do primeiro enumerador.
