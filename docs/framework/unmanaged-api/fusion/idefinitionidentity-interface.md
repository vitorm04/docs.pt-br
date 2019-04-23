---
title: Interface IDefinitionIdentity
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ff23330f307c10eac134048de39a6e19a67c75b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192661"
---
# <a name="idefinitionidentity-interface"></a>Interface IDefinitionIdentity
Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Obtém um ponteiro de interface para um novo `IDefinitionIdentity` objeto que é idêntico a este `IDefinitionIdentity`, exceto para as alterações de atributo especificado.|  
|`IDefinitionIdentity::EnumAttributes`|Obtém um ponteiro de interface para um [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) que contém os atributos associados a este objeto `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Obtém o valor do atributo com o nome especificado no namespace especificado.|  
|`IDefinitionIdentity::SetAttribute`|Define o atributo que tem o nome especificado no namespace especificado para o valor especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolation.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
