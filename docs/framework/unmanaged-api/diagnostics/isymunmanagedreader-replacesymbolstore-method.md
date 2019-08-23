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
ms.openlocfilehash: 8721f7c30061fbfd4a761bed090b761762c3c13c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939033"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>Método ISymUnmanagedReader::ReplaceSymbolStore
Substitui o repositório de símbolos existente por um repositório de símbolos delta. Esse método é semelhante ao método [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) , exceto que o Delta fornecido atua como uma substituição completa em vez de uma atualização.  
  
> [!NOTE]
> Você precisa especificar apenas um dos `filename` parâmetros ou `pIStream` , não ambos. Se `filename` for especificado, o armazenamento de símbolos será atualizado com os símbolos nesse arquivo. Se `pIStream` for especificado, o repositório será atualizado com os dados <xref:System.Runtime.InteropServices.ComTypes.IStream>do.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `filename`  
 no O nome do arquivo que contém o armazenamento de símbolo.  
  
 `pIStream`  
 no O fluxo de arquivos, usado como uma alternativa ao `filename` parâmetro.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
