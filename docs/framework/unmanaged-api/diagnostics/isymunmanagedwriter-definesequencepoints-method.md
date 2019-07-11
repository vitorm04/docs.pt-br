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
ms.openlocfilehash: f07685351425a4685ac4a0c8e1b8e3c198b14187
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777304"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>Método ISymUnmanagedWriter::DefineSequencePoints
Define um grupo de pontos de sequência dentro do método atual. Cada linha de início e a coluna inicial definem o início de uma instrução dentro de um método. Cada um final de linha e coluna de término definem o final de uma instrução dentro de um método. As matrizes devem ser classificadas em ordem crescente de deslocamentos. O deslocamento é sempre medido desde o início do método, em bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
