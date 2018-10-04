---
title: Configurando a serialização em um serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 67d8807e5ff45db2e8662586861d969e14ceaa8d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583681"
---
# <a name="configuring-serialization-in-a-workflow-service"></a>Configurando a serialização em um serviço de fluxo de trabalho
Serviços de fluxo de trabalho são serviços do Windows Communication Foundation (WCF) e, portanto a opção de usar o <xref:System.Runtime.Serialization.DataContractSerializer> (o padrão) ou o <xref:System.Xml.Serialization.XmlSerializer>. Ao gravar o fluxo de trabalho não serviços o tipo de serializador a ser usado é especificado no contrato de serviço ou operação. Durante a criação de serviços de fluxo de trabalho do WCF não especificar esses contratos no código, mas em vez disso, eles são gerados em tempo de execução por inferência do contrato. Para obter mais informações sobre a inferência do contrato, consulte [utilizando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  O serializador é especificado usando o <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> propriedade. Isso pode ser definido no designer como mostrado na ilustração a seguir.  
  
 ![Definindo o serializador](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")  
  
 O serializador também pode ser definido no código conforme mostrado no exemplo a seguir,  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 Tipos conhecidos podem ser especificados em serviços de fluxo de trabalho também. Para obter mais informações sobre os tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Tipos conhecidos podem ser especificados no designer ou no código. Para especificar os tipos conhecidos no designer, clique no botão de reticências ao lado da propriedade KnownTypes na janela Propriedades para um <xref:System.ServiceModel.Activities.Receive> atividade, como mostrado na ilustração a seguir.  
  
 ![Propriedade KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")  
  
 Isso exibirá o Editor de coleções de tipo que permitirá que você procure e especificar os tipos conhecidos.  
  
 ![Adicionando tipos conhecidos](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")  
  
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
