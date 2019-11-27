---
title: Método LinkResource
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
ms.openlocfilehash: 9e91d990a8f23335248043c59eb210e8c4155e3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445622"
---
# <a name="linkresource-method"></a>Método LinkResource
Links em um recurso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `AssemblyID`  
 ID do assembly.  
  
 `pszFileName`  
 Nome do arquivo.  
  
 `pszNewLocation`  
 Novo nome de arquivo opcional. Se não for nulo, `pszFileName` será copiado para pszNewLocation.  
  
 `pszResourceName`  
 Nome do recurso.  
  
 `dwFlags`  
 Sinalizadores de acessibilidade, como `mrPublic` e `mrPrivate`. Esse parâmetro pode ser passado para o [método DefineManifestResource](../metadata/imetadataassemblyemit-definemanifestresource-method.md).  
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 Requer ALink. h.  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
