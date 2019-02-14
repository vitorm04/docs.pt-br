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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3d7555ec5b87957ff1c8e085a4c3ac44c660b0c
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260810"
---
# <a name="strongnameerrorinfo-function"></a>Função StrongNameErrorInfo
Obtém o último código de erro que foi gerado por uma das funções de nome forte.  
  
 Essa função foi preterida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>Valor de retorno  
 O último COM código de erro definido por uma das funções de nome forte.  
  
## <a name="remarks"></a>Comentários  
 A maioria dos métodos de nome forte retorna um simples `true` ou `false` indicação da conclusão bem-sucedida. Use o `StrongNameErrorInfo` função para recuperar um HRESULT que especifica o último erro gerado pelas funções de nome forte.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
