---
title: "Método ICLRStrongName::StrongNameKeyInstall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyInstall
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 241421761b87bf9f3baf7315c2ac8e9ebd499486
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a>Método ICLRStrongName::StrongNameKeyInstall
Importa um par de chaves pública/privada para um contêiner.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszKeyContainer`  
 [in] O nome do contêiner de chave. `wszKeyContainer`deve ser uma cadeia de caracteres não vazia.  
  
 `pbKeyBlob`  
 [in] O par de chaves binário.  
  
 `cbKeyBlob`  
 [in] O tamanho, em bytes, de `pbKeyBlob`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).  
  
## <a name="remarks"></a>Comentários  
 Use o [Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) método para excluir o contêiner de chave.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
