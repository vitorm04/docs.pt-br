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
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="8c4b5-102">Configurando a serialização em um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8c4b5-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="8c4b5-103">Serviços de fluxo de trabalho são serviços do Windows Communication Foundation (WCF) e, portanto a opção de usar o <xref:System.Runtime.Serialization.DataContractSerializer> (o padrão) ou o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="8c4b5-104">Ao gravar o fluxo de trabalho não serviços o tipo de serializador a ser usado é especificado no contrato de serviço ou operação.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="8c4b5-105">Durante a criação de serviços de fluxo de trabalho do WCF não especificar esses contratos no código, mas em vez disso, eles são gerados em tempo de execução por inferência do contrato.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="8c4b5-106">Para obter mais informações sobre a inferência do contrato, consulte [utilizando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8c4b5-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="8c4b5-107">O serializador é especificado usando o <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="8c4b5-108">Isso pode ser definido no designer como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Definindo a propriedade SerializerOption na janela Propriedades.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="8c4b5-110">O serializador também pode ser definido no código conforme mostrado no exemplo a seguir,</span><span class="sxs-lookup"><span data-stu-id="8c4b5-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="8c4b5-111">Tipos conhecidos podem ser especificados em serviços de fluxo de trabalho também.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="8c4b5-112">Para obter mais informações sobre os tipos conhecidos, consulte [tipos conhecidos de contrato de dados](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="8c4b5-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="8c4b5-113">Tipos conhecidos podem ser especificados no designer ou no código.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="8c4b5-114">Para especificar os tipos conhecidos no designer, clique no botão de reticências ao lado da propriedade KnownTypes na **janela de propriedades** para um <xref:System.ServiceModel.Activities.Receive> atividade, como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>   
  
 ![Captura de tela da caixa de diálogo de propriedade KnownTypes.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="8c4b5-116">Isso exibe o Editor de coleções de tipo que permite que você pesquise e especificar os tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Captura de tela do Editor de coleções de tipo.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="8c4b5-118">Clique o **adicionar novo tipo** link e use a lista suspensa para selecionar ou pesquisar um tipo para adicionar à coleção de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="8c4b5-119">Para especificar os tipos conhecidos no uso de código a <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> propriedade conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8c4b5-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
