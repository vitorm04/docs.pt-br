---
title: Função StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecd52fce8033876f0599fa0ba25fae0850c0e01f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508466"
---
# <a name="strongnamekeyinstall-function"></a>Função StrongNameKeyInstall
Importa um par de chaves públicas/privadas em um contêiner.  
  
 Essa função foi preterida. Use o [iclrstrongname:: Strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszKeyContainer`  
 [in] O nome do contêiner de chave. `wszKeyContainer` deve ser uma cadeia de caracteres não vazia.  
  
 `pbKeyBlob`  
 [in] O par de chaves binário.  
  
 `cbKeyBlob`  
 [in] O tamanho, em bytes, do `pbKeyBlob`.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Use o [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) função para excluir o contêiner de chave.  
  
 Se o `StrongNameKeyInstall` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** WindSee [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Método StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [Método StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
