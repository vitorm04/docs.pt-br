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
ms.openlocfilehash: 735b33ac1f049f8d4d3740239e7c34a6fa16dd32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969163"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>Método ISymUnmanagedWriter::DefineSequencePoints
Define um grupo de pontos de sequência dentro do método atual. Cada linha de início e a coluna inicial definem o início de uma instrução dentro de um método. Cada um final de linha e coluna de término definem o final de uma instrução dentro de um método. As matrizes devem ser classificadas em ordem crescente de deslocamentos. O deslocamento é sempre medido desde o início do método, em bytes.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `document`  
 [in] O objeto de documento para o qual os pontos de sequência estão sendo definidos.  
  
 `spCount`  
 [in] Um `ULONG32` que indica o tamanho de cada um dos `offsets`, `lines`, `columns`, `endLines`, e `endColumns` buffers.  
  
 `offsets`  
 [in] O deslocamento dos pontos de sequência medidos do início do método.  
  
 `lines`  
 [in] Os números de linha inicial dos pontos de sequência.  
  
 `columns`  
 [in] Os números da coluna inicial dos pontos de sequência.  
  
 `endLines`  
 [in] Os números de linha finais dos pontos de sequência. Esse parâmetro é opcional.  
  
 `endColumns`  
 [in] Os números da coluna finais dos pontos de sequência. Esse parâmetro é opcional.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
