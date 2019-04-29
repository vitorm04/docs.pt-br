---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795467"
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange Bindings
Este tópico descreve como as associações de troca de metadados padrão são construídas para vários transportes.  
  
## <a name="the-default-bindings"></a>As associações padrão  
  
|Nome da associação padrão|Como a associação é construída|  
|--------------------------|------------------------------------|  
|mexHttpBinding|Um <xref:System.ServiceModel.WSHttpBinding> com segurança em nível de transporte desabilitada.|  
|mexHttpsBinding|Um <xref:System.ServiceModel.WSHttpBinding> que dá suporte à segurança em nível de transporte.|  
|mexNamedPipeBinding|Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> usando os valores padrão.|  
|mexTcpBinding|Um <xref:System.ServiceModel.Channels.CustomBinding> com um <xref:System.ServiceModel.Channels.TcpTransportBindingElement> usando valores padrão.|
