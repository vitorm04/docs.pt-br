---
title: Interface IAssemblyName
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796558"
---
# <a name="iassemblyname-interface"></a>Interface IAssemblyName
Fornece métodos para descrever e trabalhar com a identidade exclusiva de um assembly.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](iassemblyname-clone-method.md)|Cria uma cópia superficial desse `IAssemblyName` objeto.|  
|[Método Finalize](iassemblyname-finalize-method.md)|Permite que `IAssemblyName` este objeto libere recursos e execute outras operações de limpeza antes que seu destruidor seja chamado.|  
|[Método GetDisplayName](iassemblyname-getdisplayname-method.md)|Obtém o nome legível do assembly referenciado por este `IAssemblyName` objeto.|  
|[Método GetName](iassemblyname-getname-method.md)|Obtém o nome simples e não criptografado do assembly referenciado por `IAssemblyName` esse objeto.|  
|[Método GetProperty](iassemblyname-getproperty-method.md)|Obtém um ponteiro para a propriedade referenciada pelo especificado `PropertyId`.|  
|[Método GetVersion](iassemblyname-getversion-method.md)|Obtém as informações de versão do assembly referenciado por `IAssemblyName` este objeto.|  
|[Método IsEqual](iassemblyname-isequal-method.md)|Determina se um objeto `IAssemblyName` especificado é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificados.|  
|[Método SetProperty](iassemblyname-setproperty-method.md)|Define o valor da propriedade referenciada pelo especificado `PropertyId`.|  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Interface IAssemblyEnum](iassemblyenum-interface.md)
