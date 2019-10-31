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
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134325"
---
# <a name="iassemblyname-interface"></a>Interface IAssemblyName
Fornece métodos para descrever e trabalhar com a identidade exclusiva de um assembly.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Clone](iassemblyname-clone-method.md)|Cria uma cópia superficial deste `IAssemblyName` objeto.|  
|[Método Finalize](iassemblyname-finalize-method.md)|Permite que este `IAssemblyName` objeto libere recursos e execute outras operações de limpeza antes que seu destruidor seja chamado.|  
|[Método GetDisplayName](iassemblyname-getdisplayname-method.md)|Obtém o nome legível do assembly referenciado por este `IAssemblyName` objeto.|  
|[Método GetName](iassemblyname-getname-method.md)|Obtém o nome simples e não criptografado do assembly referenciado por este `IAssemblyName` objeto.|  
|[Método GetProperty](iassemblyname-getproperty-method.md)|Obtém um ponteiro para a propriedade referenciada pelo `PropertyId`especificado.|  
|[Método GetVersion](iassemblyname-getversion-method.md)|Obtém as informações de versão para o assembly referenciado por este objeto de `IAssemblyName`.|  
|[Método IsEqual](iassemblyname-isequal-method.md)|Determina se um objeto de `IAssemblyName` especificado é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificados.|  
|[Método SetProperty](iassemblyname-setproperty-method.md)|Define o valor da propriedade referenciada pelo `PropertyId`especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
- [Interface IAssemblyEnum](iassemblyenum-interface.md)
