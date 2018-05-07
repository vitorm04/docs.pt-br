---
title: Método IAssemblyCacheItem::CreateStream
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8057406552525be19f8e6457de9faf841edc6e68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iassemblycacheitemcreatestream-method"></a>Método IAssemblyCacheItem::CreateStream
Cria um fluxo com o nome especificado e o formato.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFlags`  
 [in] Sinalizadores definidos no Fusion.idl.  
  
 `pszStreamName`  
 [in] O nome do fluxo a ser criado.  
  
 `dwFormat`  
 [in] O formato do arquivo a ser transmitido.  
  
 `dwFormatFlags`  
 [in] Sinalizadores de formato específicos definidos no Fusion.idl.  
  
 `ppIStream`  
 [out] Um ponteiro para o endereço do retornado [IStream](https://msdn.microsoft.com/library/aa380034.aspx) instância.  
  
 `puliMaxSize`  
 [in, opcional] O tamanho máximo do fluxo referenciado por `ppIStream`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
