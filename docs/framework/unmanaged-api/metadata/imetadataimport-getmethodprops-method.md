---
title: "Método IMetaDataImport::GetMethodProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d02369f1e401f49548f4fdb0fc177dc7403654d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmethodprops-method"></a>Método IMetaDataImport::GetMethodProps
Obtém os metadados associados com o método referenciado pelo MethodDef especificado token.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mb`  
 [in] O token MethodDef que representa o método para retornar metadados.  
  
 `pClass`  
 [out] Um ponteiro para um token de TypeDef que representa o tipo que implementa o método.  
  
 `szMethod`  
 [out] Um ponteiro para um buffer que tem o nome do método.  
  
 `cchMethod`  
 [in] O tamanho solicitado de `szMethod`.  
  
 `pchMethod`  
 [out] Um ponteiro para o tamanho em caracteres largos de `szMethod`, ou, no caso de truncamento, o número real de caracteres largos no nome do método.  
  
 `pdwAttr`  
 [out] Um ponteiro para os sinalizadores associados ao método.  
  
 `ppvSigBlob`  
 [out] Um ponteiro para a assinatura de metadados de binários do método.  
  
 `pcbSigBlob`  
 [out] Um ponteiro para o tamanho em bytes do `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Um ponteiro para o endereço virtual relativo do método.  
  
 `pdwImplFlags`  
 [out] Um ponteiro para os sinalizadores de implementação para o método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
