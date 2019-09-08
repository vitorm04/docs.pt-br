---
title: Método SetManifestFile
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787202"
---
# <a name="setmanifestfile-method"></a>Método SetManifestFile
Permite que você especifique ou redefina o arquivo de manifesto que o vinculador usa ao criar o assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pszFile`  
  
 O nome do arquivo de manifesto cujo conteúdo é colocado no blob de recursos do Win32.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="remarks"></a>Comentários  
 Chame isso antes de solicitar o Win32ResBlob. O valor do `pszFile` parâmetro é o nome do arquivo de manifesto cujo conteúdo é lido e colocado nos recursos do Win32 com a ID de RT_MANIFEST. Quando chamado usando um parâmetro de NULL, qualquer manifesto lido anteriormente é limpo. Isso permite que um redefina o estado do vinculador para o tempo de inicialização.  
  
## <a name="requirements"></a>Requisitos  
 Requer aLink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink3](ialink3-interface.md)
- [API do ALink](index.md)
- [Interface IALink](ialink-interface.md)
- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
