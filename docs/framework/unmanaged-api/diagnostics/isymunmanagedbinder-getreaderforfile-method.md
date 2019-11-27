---
title: Método ISymUnmanagedBinder::GetReaderForFile
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: 94cda16466ea5a3d35a478a2ae80281e9414f719
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449365"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>Método ISymUnmanagedBinder::GetReaderForFile
Dada uma interface de metadados e um nome de arquivo, retorna a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.  
  
 Esse método abrirá o arquivo de banco de dados do programa (PDB) somente se ele estiver próximo ao arquivo executável. Essa alteração foi feita para fins de segurança. Se você precisar de uma pesquisa mais abrangente para o arquivo PDB, use o método [ISymUnmanagedBinder2:: GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `importer`  
 no Um ponteiro para a interface de importação de metadados.  
  
 `fileName`  
 no Um ponteiro para o nome do arquivo.  
  
 `searchPath`  
 no Um ponteiro para o caminho de pesquisa.  
  
 `pRetVal`  
 fora Um ponteiro que é definido para a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retornada.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Cabeçalho:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [Método GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
