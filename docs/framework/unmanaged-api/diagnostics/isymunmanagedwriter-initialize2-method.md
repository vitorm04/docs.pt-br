---
title: Método ISymUnmanagedWriter::Initialize2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac76ef58badcc8e443279415b7239c0b6017af3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedwriterinitialize2-method"></a>Método ISymUnmanagedWriter::Initialize2
Define a interface do emissor de metadados com a qual este gravador será associado e define o nome do arquivo de saída que serão gravados os símbolos de depuração. Esse método também permite definir o local final do arquivo de banco de dados (PDB) do programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `emitter`  
 [in] Um ponteiro para a interface do emissor de metadados.  
  
 `tempfilename`  
 [in] Um ponteiro para um `WCHAR` que contém o nome do arquivo no qual os símbolos de depuração são gravados. Se um nome de arquivo for especificado para um gravador que não use nomes de arquivo, esse parâmetro será ignorado.  
  
 `pIStream`  
 [in] Se especificado, o gravador de símbolo emite os símbolos para o determinado <xref:System.Runtime.InteropServices.ComTypes.IStream> em vez de no arquivo especificado no `filename` parâmetro. O parâmetro `pIStream` é opcional.  
  
 `fFullBuild`  
 [in] `true` quando se trata de uma recriação completa; `false` quando se trata de uma compilação incremental.  
  
 `finalfilename`  
 [in] Um ponteiro para um `WCHAR` que é a cadeia de caracteres de caminho para o local final do arquivo PDB.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Método Initialize](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
