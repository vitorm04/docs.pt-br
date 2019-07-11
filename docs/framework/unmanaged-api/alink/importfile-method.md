---
title: Método ImportFile
ms.date: 03/30/2017
api_name:
- IALink.ImportFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile
helpviewer_keywords:
- ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d76e9b4e18b46d0b546d6c66fa572c35cb9fcefe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741773"
---
# <a name="importfile-method"></a>Método ImportFile
Importa os assemblies e módulos não associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pszFilename`  
 Nome totalmente qualificado do arquivo a ser importado.  
  
 `pszTargetName`  
 Nome de arquivo de saída opcional que pode ser usado para renomear o arquivo conforme ele é vinculado no assembly.  
  
 `fSmartImport`  
 Se for TRUE, ImportTypes é usado, caso contrário, a importação deve ser executada manualmente.  
  
 `pImportToken`  
 Ponteiro para o token onde uma identificação exclusiva do arquivo será armazenada. O arquivo pode ser um assembly ou um arquivo.  
  
 `ppAssemblyScope`  
 Recebe um ponteiro para [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md). Pode ser NULL se o arquivo não é um assembly.  
  
 `pdwCountOfScopes`  
 Ponteiro para a contagem de arquivos e/ou escopos que foram importados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
