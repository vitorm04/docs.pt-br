---
title: Método ISymUnmanagedDocument::FindClosestLine
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 0e95255479792c7056bee7ee4f6c507e0f41eb6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449222"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a>Método ISymUnmanagedDocument::FindClosestLine
Retorna a linha mais próxima que é um ponto de sequência, dada uma linha neste documento que pode ou não ser um ponto de sequência.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `line`  
 no Uma linha neste documento.  
  
 `pRetVal`  
 fora Um ponteiro para uma variável que recebe a linha.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, um código de erro.  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
