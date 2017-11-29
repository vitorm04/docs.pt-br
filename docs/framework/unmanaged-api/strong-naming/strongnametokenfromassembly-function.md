---
title: "Função StrongNameTokenFromAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameTokenFromAssembly
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameTokenFromAssembly
helpviewer_keywords: StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a4d3e17f1dedd6ab346f3773f49b89d486b66e25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnametokenfromassembly-function"></a>Função StrongNameTokenFromAssembly
Cria um token de nome forte do arquivo de assembly especificado.  
  
 Essa função foi preterida. Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszFilePath`  
 [in] O caminho para o arquivo PE (executável portátil) para o assembly.  
  
 `ppbStrongNameToken`  
 [out] O token de nome forte retornado.  
  
 `pcbStrongNameToken`  
 [out] O tamanho, em bytes, do token de nome forte.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Um token de nome forte é a forma abreviada de uma chave pública. O token é um hash de 64 bits que é criado a partir de chave pública usada para assinar o assembly. O token é uma parte do nome forte do assembly e pode ser lidos dos metadados do assembly.  
  
 Depois que o token é criado, você deve chamar o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função para liberar a memória alocada.  
  
 Se o `StrongNameTokenFromAssembly` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [Método StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
