---
title: "Como: Crie um participante personalizado de persistência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebc83f100b4303b73ba2e6d3dc41d0f82e8f2c22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Como: Crie um participante personalizado de persistência
O seguinte procedimento tem as etapas para criar um participante de persistência. Consulte o [participantes de persistência](http://go.microsoft.com/fwlink/?LinkID=177735) exemplo e [repositório extensibilidade](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tópico para implementações de exemplo de participantes de persistência.  
  
1.  Crie uma classe que deriva de <xref:System.Activities.Persistence.PersistenceParticipant> ou classe de <xref:System.Activities.Persistence.PersistenceIOParticipant> . A classe de PersistenceIOParticipant oferece os mesmos pontos de extensibilidade que a classe de PersistenceParticipant além de poder participar em operações de E/S. Execute uma ou mais das seguintes etapas.  
  
2.  Implementar o método de <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> . O **CollectValues** método tem parâmetros de dicionário de dois, um para armazenar valores de leitura/gravação e o outro para armazenar valores somente gravação (usados posteriormente em consultas). Nesse método, você deve preencher esses dicionários com dados que são específicos para um participante de persistência. Cada dicionário contém o nome do valor como a chave e o valor próprio como um objeto de <xref:System.Runtime.DurableInstancing.InstanceValue> .  
  
     Os valores no dicionário readWriteValues são empacotados como **InstanceValue** objetos. Os valores no dicionário de somente gravação são empacotados como **InstanceValue** InstanceValueOptions.Optional e InstanceValueOption.WriteOnly o conjunto de objetos. Cada **InstanceValue** fornecidos pelo **CollectValues** implementações em todos os participantes de persistência devem ter um nome exclusivo.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Implementar o método de <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> . O **MapValues** método aceita dois parâmetros que são semelhantes aos parâmetros que o **CollectValues** método recebe. Todos os valores coletados no **CollectValues** estágio são passadas para esses parâmetros de dicionário. Os novos valores adicionados pelo **MapValues** estágio são adicionados aos valores somente gravação.  O dicionário somente gravação é usado para fornecer dados para uma fonte externa associada não diretamente com os valores da instância. Cada valor fornecido pelas implementações do **MapValues** método em todos os participantes de persistência deve ter um nome exclusivo.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     O método de <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> fornece funcionalidade que o <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> contrário, que permite uma dependência em outro valor fornecido por outro participante de persistência que não é processado pelo <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> ainda.  
  
4.  Implementar o **PublishValues** método. O **PublishValues** método recebe um dicionário que contém todos os valores de carregados do armazenamento de persistência.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Implementar o **BeginOnSave** método se o participante é um participante de e/s de persistência. Este método é chamado durante uma operação de salvar. Nesse método, você deve executar a adjunção de E/S a instâncias definição de fluxo de trabalho (salvar).  Se o host está usando uma transação para o comando correspondente de persistência, a mesma transação é fornecida em Transaction.Current.  Além disso, PersistenceIOParticipants pode anunciar um requisito transacional de consistência, nesse caso o host cria uma transação para o episódio de persistência se não seria usado de outra maneira.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implementar o **BeginOnLoad** método se o participante é um participante de e/s de persistência. Este método é chamado durante uma operação de carregamento. Nesse método, você deve executar a adjunção de E/S a carga de instâncias de fluxo de trabalho. Se o host está usando uma transação para o comando correspondente de persistência, a mesma transação é fornecida em Transaction.Current. Além disso, os participantes de E/S de persistência podem anunciar um requisito transacional de consistência, nesse caso o host cria uma transação para o episódio de persistência se não seria usado de outra maneira.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
