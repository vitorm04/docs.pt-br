---
title: "Método ISymUnmanagedBinder::GetReaderForFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c50bb4ca36043fc2491c9a0615b682c94c422e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a>Método ISymUnmanagedBinder::GetReaderForFile
Dado uma interface de metadados e um nome de arquivo, retorna o correto <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> estrutura que lerá os símbolos de depuração associados com o módulo.  
  
 Esse método abrirá o arquivo de programa (PDB) de banco de dados somente se ele está ao lado do arquivo executável. Essa alteração foi feita para fins de segurança. Se você precisar de uma pesquisa mais abrangente para o arquivo PDB, use o [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `importer`  
 [in] Um ponteiro para a interface de importação de metadados.  
  
 `fileName`  
 [in] Um ponteiro para o nome do arquivo.  
  
 `searchPath`  
 [in] Um ponteiro para o caminho de pesquisa.  
  
 `pRetVal`  
 [out] Um ponteiro que está definido para retornado <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [Método GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
