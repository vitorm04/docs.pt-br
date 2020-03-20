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
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="fbb80-102">Configurando a serialização em um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="fbb80-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="fbb80-103">Os serviços de fluxo de trabalho são serviços da Windows <xref:System.Runtime.Serialization.DataContractSerializer> Communication Foundation (WCF) e, portanto, têm a opção de usar o (o padrão) ou o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fbb80-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fbb80-104">Ao escrever serviços de fluxo de trabalho, o tipo de serializador a ser usado é especificado no contrato de serviço ou operação.</span><span class="sxs-lookup"><span data-stu-id="fbb80-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="fbb80-105">Ao criar serviços de fluxo de trabalho WCF, você não especifica esses contratos em código, mas sim eles são gerados em tempo de execução por inferência contratual.</span><span class="sxs-lookup"><span data-stu-id="fbb80-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="fbb80-106">Para obter mais informações sobre inferência contratual, consulte [Usando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="fbb80-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="fbb80-107">O serializador é <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> especificado usando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="fbb80-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="fbb80-108">Isso pode ser definido no designer como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fbb80-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Definindo a propriedade SerializerOption na janela Propriedades.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="fbb80-110">O serializador também pode ser definido em código, como mostrado no exemplo a seguir,</span><span class="sxs-lookup"><span data-stu-id="fbb80-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="fbb80-111">Os tipos conhecidos também podem ser especificados nos serviços workflow.</span><span class="sxs-lookup"><span data-stu-id="fbb80-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="fbb80-112">Para obter mais informações sobre tipos conhecidos, consulte [Data Contract Known Types](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fbb80-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="fbb80-113">Tipos conhecidos podem ser especificados no designer ou em código.</span><span class="sxs-lookup"><span data-stu-id="fbb80-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="fbb80-114">Para especificar tipos conhecidos no designer, clique no botão elipse ao <xref:System.ServiceModel.Activities.Receive> lado da propriedade KnownTypes na Janela **propriedades** para obter uma atividade conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="fbb80-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![Captura de tela da caixa de diálogo de propriedade KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="fbb80-116">Isso exibe o Editor de Coleções de Tipos que permite pesquisar e especificar tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="fbb80-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Captura de tela do Editor de Coleções de Tipo.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="fbb80-118">Clique no **link Adicionar novo tipo** e use o drop down para selecionar ou procurar um tipo para adicionar à coleção de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="fbb80-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="fbb80-119">Para especificar tipos conhecidos no código, use a <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> propriedade como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fbb80-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
