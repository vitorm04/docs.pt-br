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
ms.openlocfilehash: d141d23f02b2abc92e3d4455aebe1a4057b6bb85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426467"
---
# <a name="isymunmanagedreaderinitialize-method"></a>Método ISymUnmanagedReader::Initialize
Inicializa o leitor de símbolo com a interface de Importador de metadados que este leitor será associado, juntamente com o nome de arquivo do módulo.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `importer`  
 [in] A interface de Importador de metadados com a qual este leitor será associado.  
  
 `filename`  
 [in] O nome do arquivo do módulo. Você pode usar o `pIStream` parâmetro em vez disso.  
  
 `searchPath`  
 [in] Caminho de pesquisa. Esse parâmetro é opcional.  
  
 `pIStream`  
 [in] O fluxo de arquivos, usado como uma alternativa para o parâmetro de nome de arquivo.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="remarks"></a>Comentários  
 Você precisa especificar apenas um o `filename` ou `pIStream` parâmetros, não ambos. O parâmetro `searchPath` é opcional.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
