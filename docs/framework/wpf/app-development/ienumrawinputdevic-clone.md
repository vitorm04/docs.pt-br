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
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Cria outro enumerador de dispositivos de entrada raw com o mesmo estado do enumerador atual para iterar sobre a mesma lista.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppenum`  
  
 [out] Endereço da variável de saída que recebe o [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) ponteiro de interface. Se o método for bem-sucedida, o valor dessa variável de saída é indefinido.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: Esse método oferece suporte a valores de retorno padrão E_INVALIDARG, E_OUTOFMEMORY e E_UNEXPECTED.  
  
## <a name="remarks"></a>Comentários  
 Esse método torna possível registrar um ponto na sequência de enumeração para retornar ao ponto em um momento posterior. O chamador deve liberar este novo enumerador separadamente do primeiro enumerador.
