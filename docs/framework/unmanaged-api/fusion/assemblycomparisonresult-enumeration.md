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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6c417eec9583ff069c9d61fa31e9c14f3931130
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778515"
---
# <a name="assemblycomparisonresult-enumeration"></a>Enumeração AssemblyComparisonResult
Indica a equivalência de duas identidades de assembly, conforme determinado pela [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) função.  
  
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
|`ACR_EquivalentFullMatch`|Indica que o assembly de todos os campos na correspondência de comparação.|  
|`ACR_EquivalentFXUnified`|Indica que os assemblies são considerados equivalentes com base na Unificação de versão (CLR) de tempo de execução linguagem comum de números de versão do assembly no .NET Framework versão 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Indica uma correspondência parcial de assemblies com base na Unificação de CLR de números de versão do assembly do .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Indica uma correspondência parcial dos assemblies.|  
|`ACR_EquivalentPartialUnified`|Indica uma correspondência parcial de assemblies com base em Unificação herdada de números de versão.|  
|`ACR_EquivalentPartialWeakNamed`|Indica uma correspondência parcial de assemblies de nomeadas simples.|  
|`ACR_EquivalentUnified`|Indica que os assemblies são considerados equivalentes com base na Unificação de CLR de números de versão em versões herdadas do .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Indica uma correspondência entre os dois assemblies nomeados simplesmente cujos números da versão foram ignorados.|  
|`ACR_NonEquivalent`|Indica que nenhuma correspondência ocorreu entre os dois assemblies.|  
|`ACR_NonEquivalentPartialVersion`|Indica que os dois assemblies correspondem, exceto para seus números de versão para correspondem apenas parcialmente.|  
|`ACR_NonEquivalentVersion`|Indica que os dois assemblies correspondem, exceto para seus números de versão, que não correspondem.|  
|`ACR_Unknown`|Indica que o motivo para não equivalência não é conhecido.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [Enumerações de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
