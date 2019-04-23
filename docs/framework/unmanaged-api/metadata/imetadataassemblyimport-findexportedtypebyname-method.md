---
title: Método IMetaDataAssemblyImport::FindExportedTypeByName
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32a7b7b498cc4e52b8be3f43ae52293de380d9f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182254"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a>Método IMetaDataAssemblyImport::FindExportedTypeByName
Obtém um ponteiro para um tipo exportado, dado seu nome e tipo de fechamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `szName`  
 [in] O nome do tipo exportado.  
  
 `mdtExportedType`  
 [in] O token de metadados para a classe delimitadora do tipo exportado. Esse valor é `mdExportedTypeNil` se exportado solicitada tipo não é um tipo aninhado.  
  
 `ptkExportedType`  
 [out] Um ponteiro para o `mdExportedType` token que representa o tipo exportado.  
  
## <a name="remarks"></a>Comentários  
 O `FindExportedTypeByName` método usa as regras padrão empregadas pelo common language runtime para resolver referências.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Como o tempo de execução localiza assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
