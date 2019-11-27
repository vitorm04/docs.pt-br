---
title: Método IMetaDataImport::GetMethodProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437467"
---
# <a name="imetadataimportgetmethodprops-method"></a>Método IMetaDataImport::GetMethodProps
Obtém os metadados associados ao método referenciado pelo token MethodDef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parâmetros  
 `mb`  
 no O token MethodDef que representa o método para o qual retornar metadados.  
  
 `pClass`  
 fora Um ponteiro para um token de TypeDef que representa o tipo que implementa o método.  
  
 `szMethod`  
 fora Um ponteiro para um buffer que tem o nome do método.  
  
 `cchMethod`  
 no O tamanho solicitado de `szMethod`.  
  
 `pchMethod`  
 fora Um ponteiro para o tamanho em caracteres largos de `szMethod`ou, no caso de truncamento, o número real de caracteres largos no nome do método.  
  
 `pdwAttr`  
 fora Um ponteiro para todos os sinalizadores associados ao método.  
  
 `ppvSigBlob`  
 fora Um ponteiro para a assinatura de metadados binários do método.  
  
 `pcbSigBlob`  
 fora Um ponteiro para o tamanho em bytes de `ppvSigBlob`.  
  
 `pulCodeRVA`  
 fora Um ponteiro para o endereço virtual relativo do método.  
  
 `pdwImplFlags`  
 fora Um ponteiro para qualquer sinalizador de implementação para o método.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
