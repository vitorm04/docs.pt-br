---
title: Estrutura FUSION_INSTALL_REFERENCE
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611b4a543a1de7c6163ec45ff7f17d07726569ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110359"
---
# <a name="fusioninstallreference-structure"></a>Estrutura FUSION_INSTALL_REFERENCE
Representa uma referência que um aplicativo faz a um assembly que o aplicativo instalado no cache de assembly global.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`cbSize`|O tamanho da estrutura em bytes.|  
|`dwFlags`|Reservado para extensibilidade futura. Esse valor deve ser 0 (zero).|  
|`guidScheme`|A entidade que adiciona a referência. Este campo pode ter um dos seguintes valores:<br /><br /> -   FUSION_REFCOUNT_MSI_GUID: O assembly é referenciado por um aplicativo que foi instalado usando o Microsoft Windows Installer. O `szIdentifier` campo é definido como `MSI`e o `szNonCanonicalData` campo é definido como `Windows Installer`. Esse esquema é usado para os assemblies do Windows lado a lado.<br />-   FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: O assembly é referenciado por um aplicativo que aparece na **adicionar ou remover programas** interface. O `szIdentifier` campo fornece o token que registra o aplicativo com o **Adicionar/remover programas** interface.<br />-   FUSION_REFCOUNT_FILEPATH_GUID: O assembly é referenciado por um aplicativo que é representado por um arquivo no sistema de arquivos. O `szIdentifier` campo fornece o caminho para esse arquivo.<br />-   FUSION_REFCOUNT_OPAQUE_STRING_GUID: O assembly é referenciado por um aplicativo que é representado somente por uma cadeia de caracteres opaca. O `szIdentifier` campo fornece essa cadeia de caracteres opaca. O cache de assembly global não verifica a existência de referências opacas quando você remove esse valor.<br />-   FUSION_REFCOUNT_OSINSTALL_GUID: Esse valor é reservado.|  
|`szIdentifier`|Uma cadeia de caracteres exclusiva que identifica o aplicativo que instalou o assembly no cache de assembly global. Seu valor depende do valor da `guidScheme` campo.|  
|`szNonCanonicalData`|Uma cadeia de caracteres que é entendida apenas pela entidade que adiciona a referência. O cache de assembly global armazena essa cadeia de caracteres, mas não usá-lo.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Cache de assembly global](../../../../docs/framework/app-domains/gac.md)
