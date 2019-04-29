---
title: Método ISymUnmanagedReader::Initialize
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 661c27b9c21f77104b8a86163d3c92d44f8a85df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669969"
---
# <a name="isymunmanagedreaderinitialize-method"></a>Método ISymUnmanagedReader::Initialize
Inicializa o leitor de símbolo com a interface do importador de metadados que esse leitor será associado, juntamente com o nome de arquivo do módulo.  
  
> [!NOTE]
>  Esse método pode ser chamado apenas uma vez e deve ser chamado antes de quaisquer outros métodos de leitor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `importer`  
 [in] A interface de Importador de metadados com o qual esse leitor será associado.  
  
 `filename`  
 [in] O nome do arquivo do módulo. Você pode usar o `pIStream` parâmetro em vez disso.  
  
 `searchPath`  
 [in] O caminho para pesquisar. Esse parâmetro é opcional.  
  
 `pIStream`  
 [in] O fluxo de arquivos, usado como uma alternativa para o parâmetro de nome de arquivo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 Você precisa especificar apenas um dos `filename` ou o `pIStream` parâmetros, não ambos. O parâmetro `searchPath` é opcional.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
