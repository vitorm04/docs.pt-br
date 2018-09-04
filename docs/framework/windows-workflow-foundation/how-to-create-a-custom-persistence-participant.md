---
title: 'Como: Crie um participante personalizado de persistência'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 8daf4924db48c79486e85660357e3b28a2583836
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558520"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Como: Crie um participante personalizado de persistência
O seguinte procedimento tem as etapas para criar um participante de persistência. Consulte a [participação na persistência](https://go.microsoft.com/fwlink/?LinkID=177735) exemplo e [extensibilidade de Store](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tópico para exemplos de implementações de participantes de persistência.  
  
1.  Crie uma classe que deriva de <xref:System.Activities.Persistence.PersistenceParticipant> ou classe de <xref:System.Activities.Persistence.PersistenceIOParticipant> . A classe de PersistenceIOParticipant oferece os mesmos pontos de extensibilidade que a classe de PersistenceParticipant além de poder participar em operações de e/s. Execute uma ou mais das seguintes etapas.  
  
2.  Implementar o método de <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> . O **CollectValues** método tem parâmetros de dicionário de dois, para armazenar os valores de leitura/gravação e o outro é para armazenar valores somente gravação (usados mais tarde em consultas). Nesse método, você deve preencher esses dicionários com dados que são específicos para um participante de persistência. Cada dicionário contém o nome do valor como a chave e o valor próprio como um objeto de <xref:System.Runtime.DurableInstancing.InstanceValue> .  
  
     Os valores no dicionário de readWriteValues são empacotados como **InstanceValue** objetos. Os valores no dicionário somente gravação são empacotados como **InstanceValue** objetos com o conjunto de conjunto e de Instancevalueoption. Cada **InstanceValue** fornecidas pelo **CollectValues** implementações por todos os participantes de persistência devem ter um nome exclusivo.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Implementar o método de <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> . O **MapValues** método utiliza dois parâmetros que são semelhantes aos parâmetros que o **CollectValues** método recebe. Todos os valores coletados na **CollectValues** estágio são passadas para esses parâmetros de dicionário. Os novos valores adicionados pela **MapValues** estágio são adicionados aos valores somente gravação.  O dicionário somente gravação é usado para fornecer dados para uma fonte externa associada não diretamente com os valores da instância. Cada valor fornecido por implementações do **MapValues** método por todos os participantes de persistência deve ter um nome exclusivo.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     O método de <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> fornece funcionalidade que o <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> contrário, que permite uma dependência em outro valor fornecido por outro participante de persistência que não é processado pelo <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> ainda.  
  
4.  Implemente a **PublishValues** método. O **PublishValues** método recebe um dicionário que contém todos os valores carregados do armazenamento de persistência.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Implemente a **BeginOnSave** método se o participante é um participante de e/s de persistência. Este método é chamado durante uma operação de salvar. Nesse método, você deve executar o suplemento do e/s de persistência (Salvar) instâncias de fluxo de trabalho.  Se o host está usando uma transação para o comando correspondente de persistência, a mesma transação é fornecida em Transaction.Current.  Além disso, PersistenceIOParticipants pode anunciar um requisito transacional de consistência, nesse caso o host cria uma transação para o episódio de persistência se não seria usado de outra maneira.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Implemente a **BeginOnLoad** método se o participante é um participante de e/s de persistência. Este método é chamado durante uma operação de carregamento. Nesse método, você deve executar o suplemento de e/s para o carregamento de instâncias de fluxo de trabalho. Se o host está usando uma transação para o comando correspondente de persistência, a mesma transação é fornecida em Transaction.Current. Além disso, os participantes de e/s de persistência podem anunciar um requisito transacional de consistência, nesse caso o host cria uma transação para o episódio de persistência se um caso contrário, não será usado.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
