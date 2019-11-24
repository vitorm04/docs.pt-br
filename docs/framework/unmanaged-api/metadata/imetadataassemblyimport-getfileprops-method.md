---
title: Método IMetaDataAssemblyImport::GetFileProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: beb697d80417b937876a0887e4376341185a47d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447218"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>Método IMetaDataAssemblyImport::GetFileProps
Obtém as propriedades do arquivo com a assinatura de metadados especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,   
    [out] LPWSTR      szName,   
    [in]  ULONG       cchName,   
    [out] ULONG       *pchName,   
    [out] const void  **ppbHashValue,   
    [out] ULONG       *pcbHashValue,   
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mdf`  
 no O `mdFile` token de metadados que representa o arquivo para o qual obter as propriedades.  
  
 `szName`  
 fora O nome simples do arquivo.  
  
 `cchName`  
 no O tamanho, em caracteres largos, de `szName`.  
  
 `pchName`  
 fora O número de caracteres largos realmente retornados em `szName`.  
  
 `ppbHashValue`  
 fora Um ponteiro para o valor de hash. Esse é o hash, usando o algoritmo SHA-1 do arquivo.  
  
 `pcbHashValue`  
 fora O número de caracteres largos no valor de hash retornado.  
  
 `pdwFileFlags`  
 fora Um ponteiro para os sinalizadores que descrevem os metadados aplicados a um arquivo. O valor de flags é uma combinação de um ou mais valores de [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) .  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataforma:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
