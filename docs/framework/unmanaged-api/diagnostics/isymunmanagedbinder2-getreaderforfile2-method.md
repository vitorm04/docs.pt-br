---
title: "Método ISymUnmanagedBinder2::GetReaderForFile2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2.GetReaderForFile2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d232bfed801a17e1ee47dee7643ae0bf21d338e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a>Método ISymUnmanagedBinder2::GetReaderForFile2
Dado uma interface de metadados e um nome de arquivo, retorna o correto <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface que lerá os símbolos de depuração associados com o módulo.  
  
 Esse método fornece uma pesquisa mais abrangente para o arquivo de banco de dados (PDB) do programa que o [Isymunmanagedbinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `importer`  
 [in] Um ponteiro para a interface de importação de metadados.  
  
 `fileName`  
 [in] Um ponteiro para o nome do arquivo.  
  
 `searchPath`  
 [in] Um ponteiro para o caminho de pesquisa.  
  
 `searchPolicy`  
 [in] Um valor de [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeração que especifica a política a ser usado ao fazer uma pesquisa de um leitor de símbolo.  
  
 `pRetVal`  
 [out] Um ponteiro que está definido para retornado <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="remarks"></a>Comentários  
 Esta versão do método pode procurar o arquivo PDB em áreas que não seja bem ao lado do módulo. A política de pesquisa pode ser controlada pela combinação [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md). Por exemplo, `AllowReferencePathAccess | AllowSymbolServerAccess` procura o PDB ao lado do arquivo executável e em um servidor de símbolos, mas não consulta o registro ou use o caminho do arquivo executável. Se o `searchPath` parâmetro for fornecido, esses diretórios sempre serão pesquisados.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISymUnmanagedBinder2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [Método GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
