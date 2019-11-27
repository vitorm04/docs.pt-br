---
title: Método IMetaDataImport::ResolveTypeRef
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431476"
---
# <a name="imetadataimportresolvetyperef-method"></a>Método IMetaDataImport::ResolveTypeRef
Resolve uma referência de <xref:System.Type> representada pelo token TypeRef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tr`  
 no O token de metadados TypeRef para retornar as informações de tipo referenciadas.  
  
 `riid`  
 no O IID da interface a ser retornada em `ppIScope`. Normalmente, isso seria IID_IMetaDataImport.  
  
 `ppIScope`  
 fora Uma interface para o escopo do módulo no qual o tipo referenciado é definido.  
  
 `ptd`  
 fora Um ponteiro para um token de TypeDef que representa o tipo referenciado.  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
> Não use esse método se vários domínios de aplicativo forem carregados. O método não respeita os limites do domínio do aplicativo. Se várias versões de um assembly forem carregadas e contiverem o mesmo tipo com o mesmo namespace, o método retornará o escopo do módulo do primeiro tipo que encontrar.  
  
 O método `ResolveTypeRef` procura a definição de tipo em outros módulos. Se a definição de tipo for encontrada, `ResolveTypeRef` retornará uma interface para esse escopo de módulo, bem como o token de TypeDef para o tipo.  
  
 Se a referência de tipo a ser resolvida tiver um escopo de resolução de AssemblyRef, o método `ResolveTypeRef` procurará uma correspondência somente nos escopos de metadados que já foram abertos com chamadas para o método [IMetaDataDispenser:: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) ou o método [IMetaDataDispenser:: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) . Isso ocorre porque `ResolveTypeRef` não pode determinar apenas o escopo de AssemblyRef em que no disco ou no cache de assembly global o assembly está armazenado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
