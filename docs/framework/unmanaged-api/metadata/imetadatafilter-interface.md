---
title: Interface IMetaDataFilter
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e1975a5063217299ddbcdce6f625d5a1285d5b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642549"
---
# <a name="imetadatafilter-interface"></a>Interface IMetaDataFilter
Fornece métodos para marcar e filtrar os tokens de metadados para evitar a repetição de ações que já foram realizadas.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método IsTokenMarked](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-istokenmarked-method.md)|Obtém um valor que indica se o token de metadados especificado foi processado.|  
|[Método MarkToken](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-marktoken-method.md)|Define um valor que indica que o token de metadados especificado foi processado.|  
|[Método UnmarkAll](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-unmarkall-method.md)|Remove as marcas de processamento de todos os tokens no escopo atual de metadados.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
