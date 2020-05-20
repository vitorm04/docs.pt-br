---
title: Método ISymUnmanagedReader::UpdateSymbolStore
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: ccc787aa1c820a486d9a513055c9c9834b90bd1a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615430"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a>Método ISymUnmanagedReader::UpdateSymbolStore
Atualiza o repositório de símbolos existente com um repositório de símbolos delta. Esse método é usado em cenários de edição e continuação para atualizar o armazenamento de símbolo para corresponder deltas ao arquivo PE (executável portátil) original.  
  
> [!NOTE]
> Você precisa especificar apenas um dos `filename` parâmetros ou `pIStream` , não ambos. Se `filename` for especificado, o armazenamento de símbolos será atualizado com os símbolos nesse arquivo. Se `pIStream` for especificado, o repositório será atualizado com os dados do <xref:System.Runtime.InteropServices.ComTypes.IStream> .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT UpdateSymbolStore (  
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
  
## <a name="see-also"></a>Veja também

- [Interface ISymUnmanagedReader](isymunmanagedreader-interface.md)
