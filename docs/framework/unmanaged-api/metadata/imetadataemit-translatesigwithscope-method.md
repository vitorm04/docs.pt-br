---
title: "Método IMetaDataEmit::TranslateSigWithScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.TranslateSigWithScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5127defc97423283b52b7b5bd8c6b7a31104fbc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a>Método IMetaDataEmit::TranslateSigWithScope
Importa um assembly para o escopo atual e obtém uma nova assinatura de metadados para o escopo mesclado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAssemImport`  
 [in] A interface para o assembly de importação (onde a assinatura é definida).  
  
 `pbHashValue`  
 [in] O blob de hash para o assembly.  
  
 `cbHashValue`  
 [in] A contagem de bytes em `pbHashValue`.  
  
 `import`  
 [in] A interface para o escopo de metadados de importação.  
  
 `pbSigBlob`  
 [in] A assinatura a ser importado.  
  
 `cbSigBlob`  
 [in] O tamanho, em bytes, de `pbSigBlob`.  
  
 `pAssemEmit`  
 [in] A interface para o assembly de exportação.  
  
 `emit`  
 [in] A interface para o escopo de metadados de exportação.  
  
 `pvTranslatedSig`  
 [out] O buffer para armazenar o blob de assinatura traduzidos.  
  
 `cbTranslatedSigMax`  
 [in] A capacidade, em bytes, de `pvTranslatedSig`.  
  
 `pcbTranslatedSig`  
 [out] O número de bytes reais na assinatura traduzida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
