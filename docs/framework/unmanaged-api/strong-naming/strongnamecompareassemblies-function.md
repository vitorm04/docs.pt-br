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
ms.openlocfilehash: b0c2e8e46c7bb3a5e693c9ea16e6c5a0722b1898
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799155"
---
# <a name="strongnamecompareassemblies-function"></a>Função StrongNameCompareAssemblies
Determina se dois assemblies diferem somente por suas assinaturas de nome forte.  
  
 Esta função foi preterida. Em vez disso, use o método [ICLRStrongName:: StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) .  
  
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
 no O caminho para o primeiro assembly.  
  
 `wszAssembly2`  
 no O caminho para o segundo assembly.  
  
 `pdwResult`  
 fora Um dos seguintes valores:  
  
- `SN_CMP_DIFFERENT`(0)-especifica que os assemblies contêm dados diferentes.  
  
- `SN_CMP_IDENTICAL`(1)-especifica que os assemblies são exatamente iguais, incluindo suas assinaturas e soma de verificação.  
  
- `SN_CMP_SIGONLY`(2)-especifica que os assemblies diferem somente por assinatura e soma de verificação.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`após a conclusão bem-sucedida; caso contrário `false`,.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** StrongName.h  
  
 **Biblioteca** Incluído como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Comentários  
 A assinatura de nome forte de um assembly consiste no nome de texto, versão, cultura e token de chave pública do assembly.  
  
 Se a `StrongNameCompareAssemblies` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.  
  
## <a name="see-also"></a>Consulte também

- [Método StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [Interface ICLRStrongName](../hosting/iclrstrongname-interface.md)
