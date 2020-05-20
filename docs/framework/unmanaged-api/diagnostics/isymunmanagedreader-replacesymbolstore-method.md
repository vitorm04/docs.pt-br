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
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615443"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a>Método ISymUnmanagedReader::ReplaceSymbolStore
Substitui o repositório de símbolos existente por um repositório de símbolos delta. Esse método é semelhante ao método [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) , exceto que o Delta fornecido atua como uma substituição completa em vez de uma atualização.  
  
> [!NOTE]
> Você precisa especificar apenas um dos `filename` parâmetros ou `pIStream` , não ambos. Se `filename` for especificado, o armazenamento de símbolos será atualizado com os símbolos nesse arquivo. Se `pIStream` for especificado, o repositório será atualizado com os dados do <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
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
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Confira também

- [Interface ISymUnmanagedReader](isymunmanagedreader-interface.md)
