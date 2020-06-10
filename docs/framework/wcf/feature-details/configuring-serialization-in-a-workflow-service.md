---
title: Configurando a serialização em um serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 5076f3d377a656cb96909cf8df01591dc6ab72b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597534"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="b6f14-102">Configurando a serialização em um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b6f14-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="b6f14-103">Os serviços de fluxo de trabalho são Windows Communication Foundation (WCF) e, portanto, têm a opção de usar o <xref:System.Runtime.Serialization.DataContractSerializer> (o padrão) ou o <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b6f14-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b6f14-104">Ao escrever serviços que não são de fluxo de trabalho, o tipo de serializador a ser usado é especificado no contrato de operação ou serviço.</span><span class="sxs-lookup"><span data-stu-id="b6f14-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="b6f14-105">Ao criar serviços de fluxo de trabalho WCF, você não especifica esses contratos no código, mas sim eles são gerados em tempo de execução por inferência de contrato.</span><span class="sxs-lookup"><span data-stu-id="b6f14-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="b6f14-106">Para obter mais informações sobre a inferência de contrato, consulte [usando contratos no fluxo de trabalho](using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b6f14-106">For more information about contract inference, see  [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="b6f14-107">O serializador é especificado usando a <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b6f14-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="b6f14-108">Isso pode ser definido no designer, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6f14-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Definindo a Propriedade SerializerOption na janela Propriedades.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="b6f14-110">O serializador também pode ser definido no código, conforme mostrado no exemplo a seguir,</span><span class="sxs-lookup"><span data-stu-id="b6f14-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="b6f14-111">Tipos conhecidos também podem ser especificados em serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b6f14-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="b6f14-112">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="b6f14-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="b6f14-113">Tipos conhecidos podem ser especificados no designer ou no código.</span><span class="sxs-lookup"><span data-stu-id="b6f14-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="b6f14-114">Para especificar tipos conhecidos no designer, clique no botão de reticências ao lado da propriedade KnownTypes na **janela Propriedades** de uma <xref:System.ServiceModel.Activities.Receive> atividade, conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6f14-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Captura de tela da caixa de diálogo Propriedade KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="b6f14-116">Isso exibe o editor de coleções de tipos que permite pesquisar e especificar tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="b6f14-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Captura de tela do editor de coleções de tipos.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="b6f14-118">Clique no link **Adicionar novo tipo** e use a lista suspensa para selecionar ou pesquisar um tipo para adicionar à coleção de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="b6f14-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="b6f14-119">Para especificar tipos conhecidos no código, use a <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> propriedade, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b6f14-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
