---
title: Método SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
ms.openlocfilehash: 4bfad8b985a8ef059031464e99a8004842b276c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445578"
---
# <a name="setassemblyprops-method"></a>Método SetAssemblyProps
Atribui propriedades no nível do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly.  
  
 `FileToken`  
 Arquivo que define a propriedade. Pode ser NULL se `AssemblyID` não indicar um netmodule não associado.  
  
 `Option`  
 Indica a opção a ser modificada.  
  
 `Value`  
 Novo valor da opção.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 Requer ALink. h.  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
