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
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429742"
---
# <a name="isymunmanagedreaderinitialize-method"></a>Método ISymUnmanagedReader::Initialize
Inicializa o leitor de símbolos com a interface de importador de metadados à qual esse leitor será associado, juntamente com o nome de arquivo do módulo.  
  
> [!NOTE]
> Esse método pode ser chamado apenas uma vez e deve ser chamado antes de qualquer outro método de leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `importer`  
 no A interface de importador de metadados à qual este leitor será associado.  
  
 `filename`  
 no O nome do arquivo do módulo. Em vez disso, você pode usar o parâmetro `pIStream`.  
  
 `searchPath`  
 no O caminho para pesquisar. Esse parâmetro é opcional.  
  
 `pIStream`  
 no O fluxo de arquivos, usado como uma alternativa ao parâmetro filename.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 Você precisa especificar apenas um dos parâmetros `filename` ou `pIStream`, não ambos. O parâmetro `searchPath` é opcional.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
