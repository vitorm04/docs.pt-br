---
title: "Função StrongNameSignatureSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureSize
helpviewer_keywords: StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7944763f1c1379228e715b18b563e7aa776fedac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturesize-function"></a>Função StrongNameSignatureSize
Retorna o tamanho da assinatura de nome forte. `StrongNameSignatureSize`normalmente é usado por compiladores para determinar a quantidade de espaço para reservar o arquivo durante a criação de um assembly assinado com atraso.  
  
 Essa função foi preterida. Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEAN StrongNameSignatureSize (   
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
 `true`Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Se o `StrongNameSignatureSize` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
