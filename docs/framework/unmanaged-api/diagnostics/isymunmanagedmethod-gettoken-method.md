---
title: "Método ISymUnmanagedMethod::GetToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetToken
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b3cbcd27d42928223411a31dbb68e6d1dd0391fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgettoken-method"></a>Método ISymUnmanagedMethod::GetToken
Retorna o token de metadados para esse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pToken`  
 [out] Um ponteiro para um `mdMethodDef` que recebe o tamanho, em caracteres, do buffer necessário para conter os metadados.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
