---
title: Método ISymUnmanagedWriter::Initialize
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9c38a2d87f8c8db0b77dd60460d6d00a73f41ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710983"
---
# <a name="isymunmanagedwriterinitialize-method"></a>Método ISymUnmanagedWriter::Initialize
Define a interface do emissor de metadados com o qual este gravador será associado e define o nome do arquivo de saída para o qual os símbolos de depuração serão gravados.  
  
 Esse método pode ser chamado apenas uma vez, e ele deve ser chamado antes de quaisquer outros métodos de gravador. Alguns gravadores podem exigir um nome de arquivo. No entanto, você sempre pode passar um nome de arquivo para esse método sem qualquer efeito negativo sobre os gravadores que não usam o nome do arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `emitter`  
 [in] Um ponteiro para a interface do emissor de metadados.  
  
 `filename`  
 [in] O nome do arquivo no qual os símbolos de depuração são gravados. Se um nome de arquivo for especificado para um gravador que não use nomes de arquivo, esse parâmetro será ignorado.  
  
 `pIStream`  
 [in] Se for especificado, o gravador de símbolo emitirá os símbolos para o determinado <xref:System.Runtime.InteropServices.ComTypes.IStream> em vez de para o arquivo especificado no `filename` parâmetro. O parâmetro `pIStream` é opcional.  
  
 `fFullBuild`  
 [in] `true` quando se trata de uma recompilação completa; `false` quando se trata de uma compilação incremental.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também
- [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [Método Initialize2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
