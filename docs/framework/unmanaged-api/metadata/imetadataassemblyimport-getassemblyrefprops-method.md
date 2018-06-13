---
title: Método IMetaDataAssemblyImport::GetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0810ba945c1ed5874dae79704362a399c7349604
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445816"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>Método IMetaDataAssemblyImport::GetAssemblyRefProps
Obtém o conjunto de propriedades para a referência de assembly com a assinatura de metadados especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mdar`  
 [in] O `mdAssemblyRef` token de metadados que representa a referência de assembly para o qual obter as propriedades.  
  
 `ppbPublicKeyOrToken`  
 [out] Um ponteiro para a chave pública ou token de metadados.  
  
 `pcbPublicKeyOrToken`  
 [out] O número de bytes a retornado chave pública ou token.  
  
 `szName`  
 [out] O nome simples do assembly.  
  
 `cchName`  
 [in] O tamanho, em caracteres largos, de `szName`.  
  
 `pchName`  
 [out] Um ponteiro para o número de caracteres largos realmente retornados em `szName`.  
  
 `pMetaData`  
 [out] Um ponteiro para uma estrutura ASSEMBLYMETADATA que contém os metadados do assembly.  
  
 `ppbHashValue`  
 [out] Um ponteiro para o valor de hash. Este é o hash, usando o algoritmo SHA-1, do `PublicKey` propriedade do assembly referenciado, a menos que o arfFullOriginator sinalizador do [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeração está definida.  
  
 `pcbHashValue`  
 [out] O número de caracteres largos no valor de hash retornado.  
  
 `pdwAssemblyRefFlags`  
 [out] Um ponteiro para os sinalizadores que descrevem os metadados aplicado a um assembly. O valor de sinalizadores é uma combinação de um ou mais [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valores.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna S_OK se for bem-sucedida; Caso contrário, ele retorna um dos códigos de erro definidos no arquivo de cabeçalho Winerror. h.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
