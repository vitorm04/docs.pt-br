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
ms.openlocfilehash: d3693a42db8e32a4bb7a399f8c930da011130893
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778730"
---
# <a name="strongnamecompareassemblies-function"></a>Função StrongNameCompareAssemblies
Determina se dois assemblies diferem somente por suas assinaturas de nome forte.  
  
 Essa função foi preterida. Use o [iclrstrongname:: Strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszAssembly1`  
 [in] O caminho para o assembly primeiro.  
  
 `wszAssembly2`  
 [in] O caminho para o segundo conjunto.  
  
 `pdwResult`  
 [out] Um dos seguintes valores:  
  
- `SN_CMP_DIFFERENT` (0) – Especifica que os assemblies contêm dados diferentes.  
  
- `SN_CMP_IDENTICAL` (1) - Especifica que os assemblies são exatamente os mesmos, incluindo suas assinaturas e a soma de verificação.  
  
- `SN_CMP_SIGONLY` (2) - Especifica que os assemblies diferem somente por assinatura e a soma de verificação.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` Após a conclusão bem-sucedida; Caso contrário, `false`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Comentários  
 A assinatura de um assembly de nome forte consiste em nome de texto, versão, cultura e token de chave pública do assembly.  
  
 Se o `StrongNameCompareAssemblies` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
