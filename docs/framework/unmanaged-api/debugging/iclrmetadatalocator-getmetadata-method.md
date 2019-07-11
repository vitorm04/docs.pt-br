---
title: Método ICLRMetadataLocator::GetMetadata
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 235b93f4176858372a83331730ddea8b97179cc8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738364"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>Método ICLRMetadataLocator::GetMetadata
Chamado pelo common language runtime (CLR) dados serviço de acesso para recuperar os metadados de uma imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `imagePath`  
 [in] Uma cadeia de caracteres que especifica o caminho do arquivo de imagem.  
  
 `imageTimestamp`  
 [in] O carimbo de hora do arquivo de imagem.  
  
 `imageSize`  
 [in] O tamanho do arquivo de imagem.  
  
 `mvid`  
 [in] O identificador global exclusivo da imagem.  
  
 `mdRva`  
 [in] O endereço virtual relativo (RVA) dos metadados. O endereço é relativo ao endereço de base de imagem.  
  
 `flags`  
 [in] Reservado para uso futuro.  
  
 `bufferSize`  
 [in] O tamanho do buffer no qual colocar os metadados.  
  
 `buffer`  
 [out] O buffer no qual colocar os metadados.  
  
 `dataSize`  
 [out] O tamanho dos metadados que é retornado.  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRMetadataLocator](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
