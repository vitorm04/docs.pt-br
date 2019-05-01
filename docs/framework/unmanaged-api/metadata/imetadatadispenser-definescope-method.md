---
title: Método IMetaDataDispenser::DefineScope
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76a439effad9cb3f6dcdd232590cf2196ee7ab99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044383"
---
# <a name="imetadatadispenserdefinescope-method"></a>Método IMetaDataDispenser::DefineScope
Cria uma nova área na memória na qual você pode criar novos metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `rclsid`  
 [in] O CLSID da versão de estruturas de metadados a ser criado. Esse valor deve ser CLSID_CorMetaDataRuntime para o .NET Framework versão 2.0.  
  
 `dwCreateFlags`  
 [in] Sinalizadores que especificam as opções. Esse valor deve ser zero para o .NET Framework 2.0.  
  
 `riid`  
 [in] O IID da interface de metadados desejados a serem retornadas; o chamador usará a interface para criar os novos metadados.  
  
 O valor de `riid` deve especificar uma das interfaces "emite". Os valores válidos são IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit ou IID_IMetaDataEmit2.  
  
 `ppIUnk`  
 [out] O ponteiro para a interface retornada.  
  
## <a name="remarks"></a>Comentários  
 `DefineScope` cria um conjunto de tabelas de metadados na memória, gera um GUID exclusivo (identificador de versão do módulo ou MVID) para os metadados e cria uma entrada na tabela de módulo para a unidade de compilação que está sendo emitida.  
  
 Você pode anexar atributos para o escopo de metadados como um todo usando o [imetadataemit:: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) ou [imetadataemit:: Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) método, conforme apropriado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [Interface IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [Interface IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
