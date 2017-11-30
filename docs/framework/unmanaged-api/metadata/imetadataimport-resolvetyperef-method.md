---
title: "Método IMetaDataImport::ResolveTypeRef"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 390387abef5c48b4842adcfbfca126bb8292cc28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresolvetyperef-method"></a>Método IMetaDataImport::ResolveTypeRef
Resolve um <xref:System.Type> referência representada pelo token TypeRef especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `tr`  
 [in] O token de metadados de TypeRef para retornar as informações de tipo referenciado.  
  
 `riid`  
 [in] O IID da interface para retornar em `ppIScope`. Normalmente, isso seria IID_IMetaDataImport.  
  
 `ppIScope`  
 [out] Uma interface para o escopo de módulo no qual o tipo referenciado é definido.  
  
 `ptd`  
 [out] Um ponteiro para um token de TypeDef que representa o tipo de referência.  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
>  Não use esse método se vários domínios de aplicativo são carregados. O método não respeita os limites de domínio de aplicativo. Se várias versões de um assembly são carregadas e contêm o mesmo tipo com o mesmo namespace, o método retorna o escopo de módulo do tipo primeiro encontra.  
  
 O `ResolveTypeRef` pesquisas de método para a definição de tipo em outros módulos. Se a definição do tipo for encontrada, `ResolveTypeRef` retorna uma interface para esse escopo de módulo, bem como o token de TypeDef para o tipo.  
  
 Se a referência de tipo a ser resolvido tem um escopo de resolução de AssemblyRef, o `ResolveTypeRef` método procura uma correspondência somente nos escopos de metadados que já foi aberto com chamadas para o o [Imetadatadispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)método ou o [Imetadatadispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) método. Isso ocorre porque `ResolveTypeRef` não é possível determinar de apenas o escopo de AssemblyRef onde no disco ou no cache de assembly global o assembly é armazenado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
