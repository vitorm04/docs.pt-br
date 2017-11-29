---
title: "Método ICLRStrongName::StrongNameSignatureSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureSize
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91a420e520a48f3a33c4ac8c127ccefc064c23bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a>Método ICLRStrongName::StrongNameSignatureSize
Retorna o tamanho da assinatura de nome forte. Esse método é normalmente usado por compiladores para determinar a quantidade de espaço para reservar o arquivo durante a criação de um assembly assinado com atraso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbPublicKeyBlob`  
 [in] Uma estrutura de tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.  
  
 `cbPublicKeyBlob`  
 [in] O tamanho, em bytes, de `pbPublicKeyBlob`.  
  
 `pcbSize`  
 [in] O número de bytes necessários para armazenar a assinatura de nome forte.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
