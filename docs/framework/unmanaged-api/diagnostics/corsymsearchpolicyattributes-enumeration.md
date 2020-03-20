---
title: Enumeração CorSymSearchPolicyAttributes
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: 786e53d43ecde0bc3a97fadb77184d25d41430bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178344"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a>Enumeração CorSymSearchPolicyAttributes
Especifica a diretiva a ser usada ao fazer uma pesquisa por um leitor de símbolos. Essas constantes são usadas pelos [métodos ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) e [ISymUnmanagedBinder3::GetReaderFromCallback.](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)  
  
> [!IMPORTANT]
> É um risco de segurança abrir um arquivo de banco de dados de programa (PDB) de uma fonte não confiável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`AllowRegistryAccess`|Consulta o registro de caminhos de pesquisa de símbolos.|  
|`AllowSymbolServerAccess`|Acessa um servidor símbolo.|  
|`AllowOriginalPathAccess`|Pesquisa o caminho especificado no diretório Debug.|  
|`AllowReferencePathAccess`|Procura o PDB no local onde está o arquivo .exe.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Confira também

- [Enumerações de armazenamento de símbolo de diagnóstico](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
