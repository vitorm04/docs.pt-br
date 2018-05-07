---
title: Recursos do sistema operacional exigidos pelo WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="operating-system-resources-required-by-wcf"></a>Recursos do sistema operacional exigidos pelo WCF
Windows Communication Foundation (WCF) depende de vários recursos que são fornecidos pelo sistema operacional para a função. A tabela a seguir lista esses recursos.  
  
|Recurso|Descrição|  
|--------------|-----------------|  
|Coordenador de Transações Distribuídas da Microsoft (MSDTC)|Necessário para dar suporte a transações OleTx.|  
|Serviços de Informações da Internet (IIS)|Obrigatório se você quiser usar o IIS para hospedar seu aplicativo.|  
|Serviço de Ativação de Processos do Windows (WAS)|Obrigatório se você quiser usar o WAS para hospedar seu aplicativo.|  
  
## <a name="see-also"></a>Consulte também  
 [Requisitos do sistema](../../../docs/framework/wcf/wcf-system-requirements.md)
