---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange Bindings
Este tópico descreve como as associações de troca de metadados padrão são construídas para vários transportes.  
  
## <a name="the-default-bindings"></a>As associações padrão  
  
|Nome de associação padrão|Como a associação é construída|  
|--------------------------|------------------------------------|  
|MexHttpBinding|Um <xref:System.ServiceModel.WSHttpBinding> com segurança em nível de transporte desabilitada.|  
|MexHttpsBinding|Um <xref:System.ServiceModel.WSHttpBinding> que dá suporte à segurança em nível de transporte.|  
|MexNamedPipeBinding|Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> usando os valores padrão.|  
|MexTcpBinding|Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.TcpTransportBindingElement> usando valores padrão.|
