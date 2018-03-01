---
title: "Método IMetaDataDispenser::DefineScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df7a700a5747f88f14cbfa4d10f1f4d0c2a14ab7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserdefinescope-method"></a>Método IMetaDataDispenser::DefineScope
Cria uma nova área em memória no qual você pode criar novos metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `rclsid`  
 [in] O CLSID da versão de estruturas de metadados a ser criado. Esse valor deve ser CLSID_CorMetaDataRuntime para o .NET Framework versão 2.0.  
  
 `dwCreateFlags`  
 [in] Sinalizadores que especificam as opções. Esse valor deve ser zero para o .NET Framework 2.0.  
  
 `riid`  
 [in] O IID da interface de metadados desejados a serem retornadas; o chamador usará a interface para criar os novos metadados.  
  
 O valor de `riid` deve especificar uma das interfaces de "emissão". Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit ou IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 [out] O ponteiro para a interface retornado.  
  
## <a name="remarks"></a>Comentários  
 `DefineScope`cria um conjunto de tabelas de metadados na memória, gera um GUID exclusivo (identificador de versão do módulo ou MVID) para os metadados e cria uma entrada na tabela de módulo para a unidade de compilação está sendo emitida.  
  
 Você pode anexar atributos para o escopo de metadados como um todo, usando o [: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) ou [Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) método, conforme apropriado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
