---
title: Recursos do sistema operacional exigidos pelo WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 759ab099066e300484860cf3f91d6d084ba1d339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527075"
---
# <a name="operating-system-resources-required-by-wcf"></a>Recursos do sistema operacional exigidos pelo WCF
Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para a função. A tabela a seguir lista esses recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|Coordenador de Transações Distribuídas da Microsoft (MSDTC)|Necessário para dar suporte a transações OleTx.|  
|Serviços de Informações da Internet (IIS)|Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.|  
|Serviço de Ativação de Processos do Windows (WAS)|Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.|  
  
## <a name="see-also"></a>Consulte também
- [Requisitos do sistema](../../../docs/framework/wcf/wcf-system-requirements.md)
