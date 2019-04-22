---
title: Método ISymENCUnmanagedMethod::GetLineFromOffset
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3106c6680750826306cffb31e599ee2260bf4ad7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136442"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>Método ISymENCUnmanagedMethod::GetLineFromOffset
Obtém as informações de linha associadas com um deslocamento. Se o parâmetro offset (`dwOffset`) não é um ponto de sequência, esse método obtém as informações de linha associadas com a diferença anterior.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwOffset`  
 [in] Um `ULONG32` que contém o deslocamento.  
  
 `pline`  
 [out] Um ponteiro para um `ULONG32` que recebe a linha.  
  
 `pcolumn`  
 [out] Um ponteiro para um `ULONG32` que recebe a coluna.  
  
 `pendLine`  
 [out] Um ponteiro para um `ULONG32` que recebe a linha final.  
  
 `pendColumn`  
 [out] Um ponteiro para um `ULONG32` que recebe a coluna final.  
  
 `pdwStartOffset`  
 [out] Um ponteiro para um `ULONG32` que recebe o ponto de sequência associado.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymENCUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
