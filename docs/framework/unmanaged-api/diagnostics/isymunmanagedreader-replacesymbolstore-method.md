---
title: Método ISymUnmanagedReader::ReplaceSymbolStore
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 03607cf96d73e96eef63fe62b86b50be02f34421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428189"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>Método ISymUnmanagedReader::ReplaceSymbolStore
Substitui o repositório de símbolos existente por um repositório de símbolos delta. Esse método é semelhante do [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) método, exceto pelo fato do determinado delta atua como uma substituição completa em vez de uma atualização.  
  
> [!NOTE]
>  É necessário especificar apenas uma da `filename` ou `pIStream` parâmetros, não ambos. Se `filename` for especificado, o armazenamento de símbolo será atualizado com os símbolos no arquivo. Se `pIStream` for especificado, o repositório será atualizado com os dados a partir de <xref:System.Runtime.InteropServices.ComTypes.IStream>.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `filename`  
 [in] O nome do arquivo que contém o armazenamento de símbolo.  
  
 `pIStream`  
 [in] O fluxo de arquivos, usado como uma alternativa para o `filename` parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
