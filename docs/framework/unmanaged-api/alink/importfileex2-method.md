---
title: "Método ImportFileEx2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx2
helpviewer_keywords: ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2416a630f9bd763d4d4d31170cc606b160bb854
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex2-method"></a>Método ImportFileEx2
Importa os assemblies e módulos não associados. Esse método é como [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), mas funciona mesmo se o arquivo que está sendo importado não existe no disco.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszFilename`  
 Nome do arquivo a ser importado.  
  
 `pszTargetName`  
 Nome opcional do arquivo de destino.  
  
 `pAssemblyScopeIn`  
 Escopo de importação opcional [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.  
  
 `fSmartImport`  
 Se TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.  
  
 `dwOpenFlags`  
 Sinalizadores para ser passado para [método OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Recebe uma ID exclusiva para o assembly ou arquivo.  
  
 `ppAssemblyScope`  
 Recebe o escopo de importação de assembly [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface. Pode ser NULL se o arquivo não é um assembly.  
  
 `pdwCountOfScopes`  
 Recebe o número de arquivos e/ou importados de escopos.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna S_OK se o método for bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
