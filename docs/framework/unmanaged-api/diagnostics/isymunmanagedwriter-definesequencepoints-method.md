---
title: Método ISymUnmanagedWriter::DefineSequencePoints
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1dc87b201638bab974c59722a69300977b14cf08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>Método ISymUnmanagedWriter::DefineSequencePoints
Define um grupo de pontos de sequência dentro do método atual. Cada linha de início e a coluna de início definem o início de uma instrução dentro de um método. Cada final de linha e coluna de término definem o fim de uma instrução dentro de um método. As matrizes devem ser classificadas em ordem crescente de deslocamentos. O deslocamento é sempre medido desde o início do método, em bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `document`  
 [in] O objeto de documento para o qual os pontos de sequência estão sendo definidos.  
  
 `spCount`  
 [in] Um `ULONG32` que indica o tamanho de cada uma da `offsets`, `lines`, `columns`, `endLines`, e `endColumns` buffers.  
  
 `offsets`  
 [in] O deslocamento dos pontos de sequência é medido desde o início do método.  
  
 `lines`  
 [in] Os números de linha inicial dos pontos de sequência.  
  
 `columns`  
 [in] Os números da coluna inicial dos pontos de sequência.  
  
 `endLines`  
 [in] Os números de linha final dos pontos de sequência. Esse parâmetro é opcional.  
  
 `endColumns`  
 [in] Os números da coluna final dos pontos de sequência. Esse parâmetro é opcional.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
