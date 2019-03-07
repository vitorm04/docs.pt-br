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
ms.openlocfilehash: f22927b388a62ee6025c987bb107b2dfd51da0e3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488988"
---
# <a name="setmanifestfile-method"></a>Método SetManifestFile
Permite que você especificar ou redefinir o arquivo de manifesto que o vinculador usa quando cria o assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pszFile`  
  
 O nome do arquivo de manifesto cujos conteúdos são colocados no blob de recursos do Win32.  
  
## <a name="return-value"></a>Valor de retorno  
 Se o método for bem-sucedido, retornará S_OK.  
  
## <a name="remarks"></a>Comentários  
 Chame isso antes de solicitar o Win32ResBlob. O valor da `pszFile` parâmetro é o nome do arquivo de manifesto cujos conteúdos são lidos e put nos recursos do Win32 com ID de RT_MANIFEST. Quando chamado usando um parâmetro de NULL, nenhum manifesto lida anteriormente está desmarcado. Isso permite que um para redefinir o estado do vinculador para que o tempo de inicialização.  
  
## <a name="requirements"></a>Requisitos  
 Requer aLink.h  
  
## <a name="see-also"></a>Consulte também
- [Interface IALink3](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
- [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
