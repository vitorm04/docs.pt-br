---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949585"
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
Cria outro enumerador de dispositivo brutos de entrada com o mesmo estado que o enumerador atual para iterar sobre a mesma lista.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppenum`  
  
 [out] Endereço da variável de saída que recebe o [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) ponteiro de interface. Se o método for bem-sucedido, o valor dessa variável de saída é indefinido.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: Esse método dá suporte aos valores retornados padrão E_INVALIDARG e E_OUTOFMEMORY E_UNEXPECTED.  
  
## <a name="remarks"></a>Comentários  
 Esse método torna possível registrar um ponto na sequência de enumeração para retornar a esse ponto em um momento posterior. O chamador deve liberar esse novo enumerador separadamente do primeiro enumerador.
