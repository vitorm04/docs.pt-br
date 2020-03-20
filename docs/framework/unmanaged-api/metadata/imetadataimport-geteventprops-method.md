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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177264"
---
# <a name="imetadataimportgeteventprops-method"></a>Método IMetaDataImport::GetEventProps
Obtém informações de metadados para o evento representado pelo token de evento especificado, incluindo o tipo de declaração, os métodos de adicionar e remover para delegados e quaisquer sinalizadores e outros dados associados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>parâmetros  
 `ev`  
 [em] O token de metadados do evento representando o evento para obter metadados para.  
  
 `pClass`  
 [fora] Um ponteiro para o token TypeDef representando a classe que declara o evento.  
  
 `szEvent`  
 [fora] O nome do evento `ev`referenciado por .  
  
 `pchEvent`  
 [em] O comprimento solicitado em `szEvent`caracteres amplos de .  
  
 `pdwEventFlags`  
 [fora] O comprimento retornado em `szEvent`caracteres largos de .  
  
 `ptkEventType`  
 [fora] Um ponteiro para um token de metadados TypeRef ou TypeDef representando o <xref:System.Delegate> tipo do evento.  
  
 `pmdAddOn`  
 [fora] Um ponteiro para o token de metadados representando o método que adiciona manipuladores para o evento.  
  
 `pmdRemoveOn`  
 [fora] Um ponteiro para o token de metadados representando o método que remove manipuladores para o evento.  
  
 `pmdFire`  
 [fora] Um ponteiro para o token de metadados representando o método que levanta o evento.  
  
 `rmdOtherMethod`  
 [fora] Uma matriz de ponteiros de token para outros métodos associados ao evento.  
  
 `cMax`  
 [em] O tamanho máximo `rmdOtherMethod` da matriz.  
  
 `pcOtherMethod`  
 [fora] O número de tokens `rmdOtherMethod`retornou em .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
