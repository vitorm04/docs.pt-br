---
title: Método IMetaDataAssemblyEmit::DefineManifestResource
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177864"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>Método IMetaDataAssemblyEmit::DefineManifestResource
Cria `ManifestResource` uma estrutura contendo metadados para o recurso manifesto especificado e retorna o token de metadados associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `szName`  
 [em] O nome do recurso.  
  
 `tkImplementation`  
 [em] Um token de `mdtFile` metadados do tipo ou `mdtAssemblyRef` que mapeia para o provedor de recursos. Um valor NULL indica que o arquivo no qual os metadados estão incorporados é o provedor de recursos.  
  
 `dwOffset`  
 [em] A compensação para o início do recurso dentro do arquivo. Para recursos em arquivos autônomos, isso sempre será zero. Se o recurso estiver incorporado em um arquivo PE (executável portátil), esta será uma compensação do recurso BLOB, que começa no local especificado no arquivo de cabeçalho cor.h.  
  
 `dwResourceFlags`  
 [em] Uma combinação bitwise de valores de bandeira que especificam configurações de propriedade para a definição de recurso.  
  
 `pmdmr`  
 [fora] Um ponteiro para o token de metadados retornado.  
  
## <a name="remarks"></a>Comentários  
 Uma `ManifestResource` estrutura de metadados deve ser definida para cada recurso que é implementado em cada um dos arquivos da montagem.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Consulte [os requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
