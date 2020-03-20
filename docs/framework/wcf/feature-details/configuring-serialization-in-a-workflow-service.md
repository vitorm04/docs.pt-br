---
title: Configurando a serialização em um serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185346"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Configurando a serialização em um serviço de fluxo de trabalho
Os serviços de fluxo de trabalho são serviços da Windows <xref:System.Runtime.Serialization.DataContractSerializer> Communication Foundation (WCF) e, portanto, têm a opção de usar o (o padrão) ou o <xref:System.Xml.Serialization.XmlSerializer>. Ao escrever serviços de fluxo de trabalho, o tipo de serializador a ser usado é especificado no contrato de serviço ou operação. Ao criar serviços de fluxo de trabalho WCF, você não especifica esses contratos em código, mas sim eles são gerados em tempo de execução por inferência contratual. Para obter mais informações sobre inferência contratual, consulte [Usando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  O serializador é <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> especificado usando a propriedade. Isso pode ser definido no designer como mostrado na ilustração a seguir.  
  
 ![Definindo a propriedade SerializerOption na janela Propriedades.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 O serializador também pode ser definido em código, como mostrado no exemplo a seguir,  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  Os tipos conhecidos também podem ser especificados nos serviços workflow. Para obter mais informações sobre tipos conhecidos, consulte [Data Contract Known Types](data-contract-known-types.md). Tipos conhecidos podem ser especificados no designer ou em código. Para especificar tipos conhecidos no designer, clique no botão elipse ao <xref:System.ServiceModel.Activities.Receive> lado da propriedade KnownTypes na Janela **propriedades** para obter uma atividade conforme mostrado na ilustração a seguir.
  
 ![Captura de tela da caixa de diálogo de propriedade KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Isso exibe o Editor de Coleções de Tipos que permite pesquisar e especificar tipos conhecidos.  
  
 ![Captura de tela do Editor de Coleções de Tipo.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Clique no **link Adicionar novo tipo** e use o drop down para selecionar ou procurar um tipo para adicionar à coleção de tipos conhecidos. Para especificar tipos conhecidos no código, use a <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> propriedade como mostrado no exemplo a seguir.  
  
```csharp
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```
