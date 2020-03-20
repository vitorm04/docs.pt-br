---
title: Método ISymUnmanagedScope2::GetConstants
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176611"
---
# <a name="isymunmanagedscope2getconstants-method"></a>Método ISymUnmanagedScope2::GetConstants
As constantes locais são definidas dentro deste escopo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cConstants`  
 [em] O comprimento do buffer `pcConstants` que o parâmetro aponta.  
  
 `pcConstants`  
 [fora] Um ponteiro `ULONG32` para um que recebe o tamanho, em caracteres, do buffer necessário para conter as constantes.  
  
 `constants`  
 [fora] O tampão que armazena as constantes.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método for bem sucedido; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedScope2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
