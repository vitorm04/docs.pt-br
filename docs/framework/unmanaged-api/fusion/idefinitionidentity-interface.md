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
ms.openlocfilehash: 59578e1d3a66809c86f7daad1b208df2ae09568d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108034"
---
# <a name="idefinitionidentity-interface"></a>Interface IDefinitionIdentity
Representa a assinatura exclusiva do código que define o aplicativo no escopo atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Obtém um ponteiro de interface para um novo objeto `IDefinitionIdentity` que é idêntico a este `IDefinitionIdentity`, exceto para as alterações de atributo especificadas.|  
|`IDefinitionIdentity::EnumAttributes`|Obtém um ponteiro de interface para um objeto [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) que contém os atributos associados a esse `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Obtém o valor do atributo com o nome especificado no namespace especificado.|  
|`IDefinitionIdentity::SetAttribute`|Define o atributo que tem o nome especificado no namespace especificado para o valor especificado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Isolamento. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de fusão](fusion-interfaces.md)
