---
title: Função StrongNameErrorInfo
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
ms.openlocfilehash: d5eedc34b75d3a0c02969c06454b0f7ec942ed17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176936"
---
# <a name="strongnameerrorinfo-function"></a>Função StrongNameErrorInfo
Obtém o último código de erro que foi gerado por uma das funções de nome forte.  
  
 Esta função foi preterida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameErrorInfo ();
```  
  
## <a name="return-value"></a>Valor retornado  
 O último código de erro COM definido por uma das funções de nome forte.  
  
## <a name="remarks"></a>Comentários  
 A maioria dos métodos de `true` `false` nome forte retornam uma simples ou indicação de conclusão bem sucedida. Use `StrongNameErrorInfo` a função para recuperar um HRESULT que especifica o último erro gerado pelas funções de nome forte.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
