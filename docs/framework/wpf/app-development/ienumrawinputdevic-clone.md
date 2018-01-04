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
ms.workload: dotnet
ms.openlocfilehash: db218ec824dfe163946b0c1bd412efd0f78f4ad8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
