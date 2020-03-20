---
title: Método IMetaDataEmit::TranslateSigWithScope
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 2662af41fbd2cdc3ce8a6df1e036dfc5b22ff6a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175537"
---
# <a name="imetadataemittranslatesigwithscope-method"></a>Método IMetaDataEmit::TranslateSigWithScope
Importa uma montagem no escopo atual e obtém uma nova assinatura de metadados para o escopo mesclado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>parâmetros  
 `pAssemImport`  
 [em] A interface para montagem de importação (onde a assinatura é definida).  
  
 `pbHashValue`  
 [em] A bolha de hash para a assembléia.  
  
 `cbHashValue`  
 [em] A contagem de `pbHashValue`bytes em .  
  
 `import`  
 [em] A interface para escopo de metadados de importação.  
  
 `pbSigBlob`  
 [em] A assinatura a ser importada.  
  
 `cbSigBlob`  
 [em] O tamanho, em bytes, de `pbSigBlob`.  
  
 `pAssemEmit`  
 [em] A interface para montagem de exportação.  
  
 `emit`  
 [em] A interface para escopo de metadados de exportação.  
  
 `pvTranslatedSig`  
 [fora] O buffer para segurar a bolha de assinatura traduzida.  
  
 `cbTranslatedSigMax`  
 [em] A capacidade, em bytes, de `pvTranslatedSig`.  
  
 `pcbTranslatedSig`  
 [fora] O número de bytes reais na assinatura traduzida.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
