---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767342"
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
