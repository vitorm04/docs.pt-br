---
title: Função StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd1d098f21a3d5ba43b6251c87c36df4347a924
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457555"
---
# <a name="strongnamecompareassemblies-function"></a>Função StrongNameCompareAssemblies
Determina se os dois assemblies diferem somente por suas assinaturas de nome forte.  
  
 Essa função foi preterida. Use o [: Strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `wszAssembly1`  
 [in] O caminho para o primeiro conjunto.  
  
 `wszAssembly2`  
 [in] O caminho para o segundo conjunto.  
  
 `pdwResult`  
 [out] Um dos seguintes valores:  
  
-   `SN_CMP_DIFFERENT` (0) - Especifica que os assemblies conterem dados diferentes.  
  
-   `SN_CMP_IDENTICAL` (1) - Especifica que os assemblies são exatamente iguais, incluindo suas assinaturas e a soma de verificação.  
  
-   `SN_CMP_SIGONLY` (2) - Especifica que os assemblies diferem somente por assinatura e soma de verificação.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Comentários  
 A assinatura de um assembly de nome forte consiste em nome de texto, versão, cultura e token de chave pública do assembly.  
  
 Se o `StrongNameCompareAssemblies` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="see-also"></a>Consulte também  
 [Método StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
