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
ms.openlocfilehash: 82b81ec29dece182548ead046edc7cb754fbf00e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430655"
---
# <a name="assemblycomparisonresult-enumeration"></a>Enumeração AssemblyComparisonResult
Indica a equivalência de duas identidades de assembly, conforme determinado pelo [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`ACR_EquivalentFullMatch`|Indica que o assembly todos os campos na correspondência de comparação.|  
|`ACR_EquivalentFXUnified`|Indica que os assemblies são considerados equivalentes com base na comuns Unificação de versão (CLR) de tempo de execução de linguagem de números de versão do assembly do .NET Framework versão 2.0.|  
|`ACR_EquivalentPartialFXUnified`|Indica uma correspondência parcial dos assemblies baseada a Unificação de CLR de números de versão do assembly do .NET Framework 2.0.|  
|`ACR_EquivalentPartialMatch`|Indica uma correspondência parcial dos assemblies.|  
|`ACR_EquivalentPartialUnified`|Indica uma correspondência parcial dos assemblies com base em Unificação herdada de números de versão.|  
|`ACR_EquivalentPartialWeakNamed`|Indica uma correspondência parcial de assemblies simplesmente nomeadas.|  
|`ACR_EquivalentUnified`|Indica que os assemblies são considerados equivalentes com base na Unificação de CLR de números de versão em versões herdadas do .NET Framework.|  
|`ACR_EquivalentWeakNamed`|Indica uma correspondência entre dois assemblies simplesmente nomeadas cujos números de versão foram ignorados.|  
|`ACR_NonEquivalent`|Indica que ocorreu nenhuma correspondência entre os dois assemblies.|  
|`ACR_NonEquivalentPartialVersion`|Indica que os dois assemblies correspondem, exceto seus números de versão que correspondem apenas parcialmente.|  
|`ACR_NonEquivalentVersion`|Indica que os dois assemblies correspondem, exceto seus números de versão, que não correspondem.|  
|`ACR_Unknown`|Indica que a razão para não equivalência não é conhecida.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 [Enumerações de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
