---
title: Interface IMetaDataFilter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataFilter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter
helpviewer_keywords:
- IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: ec0856ef-8c56-40ba-bf60-86e0ce8b337f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0918802a146940fb7579279e56f752bd114c746c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatafilter-interface"></a>Interface IMetaDataFilter
Fornece métodos para a marcação e a filtragem de tokens de metadados para evitar a repetição de ações que já foi usadas.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método IsTokenMarked](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|Obtém um valor que indica se o token de metadados especificado foi processado.|  
|[Método MarkToken](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|Define um valor que indica se o token de metadados especificado foi processado.|  
|[Método UnmarkAll](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|Remove as marcas de processamento de todos os tokens no escopo atual de metadados.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
