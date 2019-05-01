---
title: Configuração
ms.date: 03/30/2017
ms.assetid: 86a6e12f-73b5-450e-8725-f4ca5fe0702c
ms.openlocfilehash: 3ef91a1f851f87ebf35669748f8beb1c6a880ae8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998810"
---
# <a name="configuration"></a>Configuração
Este tópico lista todas as exceções geradas pela configuração do Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista de exceções  
  
|Código do recurso|Cadeia de caracteres de recurso|  
|-------------------|---------------------|  
|ConfigBindingCannotBeConfigured|A associação no ponto de extremidade de serviço não pode ser configurada.|  
|ConfigElementKeyNull|A chave do elemento de configuração específica não pode ser nula.|  
|ConfigExtensionTypeNotRegisteredInCollection|O tipo de extensão específica não está registrado na coleção de extensão específica.|  
|ConfigIndexOutOfRange|O valor para o atributo específico está fora do intervalo.|  
|ConfigInvalidBindingConfigurationName|A configuração específica não tem uma associação com o nome específico.|  
|ConfigInvalidBindingName|A configuração específica não tem uma associação com o nome específico. Isso é um valor inválido para a associação.|  
|ConfigInvalidCommonEndpointBehaviorType|Não é possível adicionar a extensão de comportamento específico para o comportamento de ponto de extremidade comum porque ele não implementa o tipo específico.|  
|ConfigInvalidCommonServiceBehaviorType|Não é possível adicionar a extensão de comportamento específico para o comportamento de serviço comum porque ele não implementa o tipo específico.|  
|ConfigInvalidEndpointBehaviorType|Não é possível adicionar a extensão de comportamento específico para o comportamento de ponto de extremidade específico, porque o tipo de comportamento subjacente não implementa a interface IServiceBehavior.|  
|ConfigInvalidExtensionType|O tipo específico deve derivar da extensão específica a ser usado na coleção.|  
|ConfigInvalidServiceBehaviorType|Não é possível adicionar a extensão de comportamento ' para o comportamento de serviço com o específico nome porque o tipo de comportamento subjacente não implementa a interface IServiceBehavior.|  
|ConfigMessageEncodingAlreadyInBinding|Não é possível adicionar o elemento de codificação de mensagem específica. Já existe outro elemento de codificação de mensagem na associação específica. Pode haver apenas uma mensagem de elemento para cada associação de codificação.|  
|ConfigNoExtensionCollectionAssociatedWithType|Não é possível encontrar a coleção de extensão associada com a extensão do tipo específico.|  
|ConfigSectionNotFound|A seção de configuração específico não pode ser criada. O arquivo Machine. config está faltando informações. Verifique se essa seção de configuração está registrada corretamente e que a ortografia do nome da seção. Para as seções do Windows Communication Foundation, execute ServiceModelReg.exe -i para corrigir esse erro.|  
|ConfigTransportAlreadyInBinding|Não é possível adicionar o elemento de transporte específico. Já existe outro elemento de transporte na associação específica. Pode haver apenas uma mensagem de elemento para cada associação de codificação.|
