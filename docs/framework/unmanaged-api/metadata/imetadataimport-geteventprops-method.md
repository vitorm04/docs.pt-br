---
title: "Método IMetaDataImport::GetEventProps"
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
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73f257c46fd21355eeaabbe9e1b5d2841d2c3911
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgeteventprops-method"></a>Método IMetaDataImport::GetEventProps
Obtém informações de metadados para o evento representado pelo token de evento especificado, incluindo o tipo de declaração, adicionar e remover métodos para delegados e os sinalizadores e outros dados associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ev`  
 [in] O token de metadados de evento que representa o evento para obter metadados.  
  
 `pClass`  
 [out] Um ponteiro para o token de TypeDef que representa a classe que declara o evento.  
  
 `szEvent`  
 [out] O nome do evento referenciado por `ev`.  
  
 `pchEvent`  
 [in] O tamanho solicitado em caracteres largos de `szEvent`.  
  
 `pdwEventFlags`  
 [out] O comprimento retornado em caracteres largos de `szEvent`.  
  
 `ptkEventType`  
 [out] Um ponteiro para um TypeRef ou TypeDef metadados token que representa o <xref:System.Delegate> tipo do evento.  
  
 `pmdAddOn`  
 [out] Um ponteiro para o token de metadados que representa o método que adiciona manipuladores para o evento.  
  
 `pmdRemoveOn`  
 [out] Um ponteiro para o token de metadados que representa o método que remove os manipuladores para o evento.  
  
 `pmdFire`  
 [out] Um ponteiro para o token de metadados que representa o método que gera o evento.  
  
 `rmdOtherMethod`  
 [out] Uma matriz de ponteiros de token para outros métodos associados ao evento.  
  
 `cMax`  
 [in] O tamanho máximo da `rmdOtherMethod` matriz.  
  
 `pcOtherMethod`  
 [out] O número de tokens retornados em `rmdOtherMethod`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
