---
title: Configurando a serialização em um serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 74d9a812b9e0cd51a401fa3526c947d52413807a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488866"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="443b3-102">Configurando a serialização em um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="443b3-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="443b3-103">Serviços de fluxo de trabalho são serviços do Windows Communication Foundation (WCF) e, portanto a opção de usar qualquer um de <xref:System.Runtime.Serialization.DataContractSerializer> (o padrão) ou o <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="443b3-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="443b3-104">Quando o tipo de serializador a ser usado de serviços gravar o fluxo de trabalho não é especificado no contrato de serviço ou operação.</span><span class="sxs-lookup"><span data-stu-id="443b3-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="443b3-105">Ao criar serviços de fluxo de trabalho WCF não especificar esses contratos no código, mas em vez disso, eles são gerados em tempo de execução por inferência de contrato.</span><span class="sxs-lookup"><span data-stu-id="443b3-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="443b3-106">Para obter mais informações sobre a inferência de tipos de contrato, consulte [usando contratos no fluxo de trabalho](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="443b3-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="443b3-107">O serializador é especificado usando o <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="443b3-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="443b3-108">Isso pode ser definido no designer como mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="443b3-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="443b3-109">![Definindo o serializador](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="443b3-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="443b3-110">O serializador também pode ser definido no código conforme mostrado no exemplo a seguir,</span><span class="sxs-lookup"><span data-stu-id="443b3-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
 <span data-ttu-id="443b3-111">Tipos conhecidos podem ser especificados em serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="443b3-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="443b3-112">Para obter mais informações sobre os tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="443b3-112">For more information about Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="443b3-113">Tipos conhecidos podem ser especificados no designer ou no código.</span><span class="sxs-lookup"><span data-stu-id="443b3-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="443b3-114">Para especificar os tipos conhecidos no designer, clique no botão de reticências ao lado da propriedade KnownTypes na janela Propriedades para um <xref:System.ServiceModel.Activities.Receive> atividade conforme mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="443b3-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="443b3-115">![Propriedade KnownTypes](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="443b3-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="443b3-116">Isso exibirá o Editor de coleções de tipo que permite pesquisar e especifique tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="443b3-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="443b3-117">![Adicionando tipos conhecidos](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="443b3-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="443b3-118">Clique o **adicionar novo tipo** link e use a lista suspensa para selecionar ou pesquisar um tipo para adicionar à coleção de tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="443b3-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="443b3-119">Para especificar os tipos conhecidos em uso do código de <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> propriedade conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="443b3-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="443b3-120">Para ver um exemplo de código completo que mostra como configurar a serialização de um serviço de fluxo de trabalho consulte [mensagens de formatação em serviços de fluxo de trabalho](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="443b3-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
