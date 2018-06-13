---
title: Método IMetaDataImport::GetEventProps
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac1ecb73257782888c963082953ed243177a86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448798"
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
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
