---
title: "Configuração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86a6e12f-73b5-450e-8725-f4ca5fe0702c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3eee9f955ca75d799b9e5384e47df527934a595f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration"></a>Configuração
Este tópico lista todas as exceções geradas pelo [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] configuração.  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|ConfigBindingCannotBeConfigured|A associação no ponto de extremidade de serviço não pode ser configurada.|  
|ConfigElementKeyNull|A chave de elemento de configuração específica não pode ser nula.|  
|ConfigExtensionTypeNotRegisteredInCollection|O tipo de extensão específica não está registrado na coleção de extensões específicas.|  
|ConfigIndexOutOfRange|O valor para o atributo específico está fora do intervalo.|  
|ConfigInvalidBindingConfigurationName|A configuração específica não tem uma associação com o nome específico.|  
|ConfigInvalidBindingName|A configuração específica não tem uma associação com o nome específico. Este é um valor inválido para a associação.|  
|ConfigInvalidCommonEndpointBehaviorType|Não é possível adicionar a extensão de comportamento específico para o comportamento de ponto de extremidade comum porque ela não implementa o tipo específico.|  
|ConfigInvalidCommonServiceBehaviorType|Não é possível adicionar a extensão de comportamento específico para o comportamento de serviço comum porque ela não implementa o tipo específico.|  
|ConfigInvalidEndpointBehaviorType|Não é possível adicionar a extensão de comportamento específico para o comportamento de ponto de extremidade específico porque o tipo de comportamento subjacente não implementa a interface IServiceBehavior.|  
|ConfigInvalidExtensionType|O tipo deve derivar da extensão específica a ser usado na coleção.|  
|ConfigInvalidServiceBehaviorType|Não é possível adicionar a extensão de comportamento ' ao comportamento de serviço com específico nome porque o tipo de comportamento subjacente não implementa a interface IServiceBehavior.|  
|ConfigMessageEncodingAlreadyInBinding|Não é possível adicionar o elemento de codificação de mensagem específica. Já existe outro elemento de codificação de mensagem na associação específica. Pode haver apenas uma mensagem de codificação de elemento para cada associação.|  
|ConfigNoExtensionCollectionAssociatedWithType|Não é possível encontrar a coleção de extensões associada à extensão do tipo específico.|  
|ConfigSectionNotFound|Não é possível criar a seção de configuração específico. O arquivo Machine. config está faltando informações. Verifique se essa seção de configuração está registrada corretamente e se a ortografia do nome da seção. Seções do Windows Communication Foundation, execute ServiceModelReg.exe -i para corrigir esse erro.|  
|ConfigTransportAlreadyInBinding|Não é possível adicionar o elemento de transporte específico. Já existe outro elemento de transporte na associação específica. Pode haver apenas uma mensagem de codificação de elemento para cada associação.|
