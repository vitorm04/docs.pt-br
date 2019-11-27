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
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445566"
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
  
## <a name="return-value"></a>Valor retornado  
 Retorna S_OK se o método tiver sucesso.  
  
## <a name="remarks"></a>Comentários  
 Chame isso antes de solicitar o Win32ResBlob. O valor do parâmetro `pszFile` é o nome do arquivo de manifesto cujo conteúdo é lido e colocado nos recursos do Win32 com a ID de RT_MANIFEST. Quando chamado usando um parâmetro de NULL, qualquer manifesto lido anteriormente é limpo. Isso permite que um redefina o estado do vinculador para o tempo de inicialização.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 Requer aLink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink3](ialink3-interface.md)
- [API do ALink](index.md)
- [Interface IALink](ialink-interface.md)
- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
