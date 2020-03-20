---
title: Enumeração AssemblyComparisonResult
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178298"
---
# <a name="assemblycomparisonresult-enumeration"></a>Enumeração AssemblyComparisonResult
Indica a equivalência de duas identidades de montagem, conforme determinado pela função [CompareAssemblyIdentity.](compareassemblyidentity-function.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>Membros  
  
|Nome do membro|Descrição|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|Indica que todos os campos de montagem na correspondência correspondem.|  
|`ACR_EquivalentFXUnified`|Indica que os conjuntos são considerados equivalentes com base na unificação da versão de tempo de execução (CLR) com um idioma comum dos números da versão de montagem na versão 2.0 do Framework .NET.|  
|`ACR_EquivalentPartialFXUnified`|Indica uma correspondência parcial das assembléias com base na unificação clr dos números da versão de montagem no Quadro .NET 2.0.|  
|`ACR_EquivalentPartialMatch`|Indica uma combinação parcial das assembléias.|  
|`ACR_EquivalentPartialUnified`|Indica uma correspondência parcial das assembléias baseada na unificação legado dos números das versões.|  
|`ACR_EquivalentPartialWeakNamed`|Indica uma combinação parcial de assembléias simplesmente nomeadas.|  
|`ACR_EquivalentUnified`|Indica que os conjuntos são considerados equivalentes com base na unificação clr de números de versão em versões legadas do .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Indica uma correspondência entre dois conjuntos simplesmente nomeados cujos números de versão foram ignorados.|  
|`ACR_NonEquivalent`|Indica que não houve correspondência entre as duas assembléias.|  
|`ACR_NonEquivalentPartialVersion`|Indica que os dois conjuntos correspondem, exceto os números de suas versões, que correspondem apenas parcialmente.|  
|`ACR_NonEquivalentVersion`|Indica que os dois conjuntos correspondem, exceto os números de suas versões, que não correspondem.|  
|`ACR_Unknown`|Indica que a razão para a não equivalência não é conhecida.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** Incluído como um recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função CompareAssemblyIdentity](compareassemblyidentity-function.md)
- [Enumerações Fusion](fusion-enumerations.md)
