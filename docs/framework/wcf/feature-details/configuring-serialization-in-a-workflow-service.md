---
title: Configurando a serialização em um serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843923"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Configurando a serialização em um serviço de fluxo de trabalho
Serviços de fluxo de trabalho são serviços do Windows Communication Foundation (WCF) e, portanto a opção de usar o <xref:System.Runtime.Serialization.DataContractSerializer> (o padrão) ou o <xref:System.Xml.Serialization.XmlSerializer>. Ao gravar o fluxo de trabalho não serviços o tipo de serializador a ser usado é especificado no contrato de serviço ou operação. Durante a criação de serviços de fluxo de trabalho do WCF não especificar esses contratos no código, mas em vez disso, eles são gerados em tempo de execução por inferência do contrato. Para obter mais informações sobre a inferência do contrato, consulte [utilizando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  O serializador é especificado usando o <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> propriedade. Isso pode ser definido no designer como mostrado na ilustração a seguir.  
  
 ![Definindo a propriedade SerializerOption na janela Propriedades.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 O serializador também pode ser definido no código conforme mostrado no exemplo a seguir,  
  
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
  
  Tipos conhecidos podem ser especificados em serviços de fluxo de trabalho também. Para obter mais informações sobre os tipos conhecidos, consulte [tipos conhecidos de contrato de dados](data-contract-known-types.md). Tipos conhecidos podem ser especificados no designer ou no código. Para especificar os tipos conhecidos no designer, clique no botão de reticências ao lado da propriedade KnownTypes na **janela de propriedades** para um <xref:System.ServiceModel.Activities.Receive> atividade, como mostrado na ilustração a seguir.   
  
 ![Captura de tela da caixa de diálogo de propriedade KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 Isso exibe o Editor de coleções de tipo que permite que você pesquise e especificar os tipos conhecidos.  
  
 ![Captura de tela do Editor de coleções de tipo.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 Clique o **adicionar novo tipo** link e use a lista suspensa para selecionar ou pesquisar um tipo para adicionar à coleção de tipos conhecidos. Para especificar os tipos conhecidos no uso de código a <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> propriedade conforme mostrado no exemplo a seguir.  
  
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
