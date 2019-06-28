---
title: Controle de versão lado a lado no WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 0dfb2469ac3f497a40a3008c9933977947685979
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425495"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="8d09a-102">Controle de versão lado a lado no WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="8d09a-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="8d09a-103">O <xref:System.ServiceModel.Activities.WorkflowServiceHost> lado a lado de controle de versão introduzido no .NET Framework 4.5 fornece a capacidade de hospedar várias versões de um serviço de fluxo de trabalho em um único ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="8d09a-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in .NET Framework 4.5 provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="8d09a-104">A funcionalidade de lado a lado fornecida permite que um serviço de fluxo de trabalho seja configurado para que novas instâncias do serviço de fluxo de trabalho sejam criadas usando a nova definição de fluxo de trabalho, enquanto executa instâncias completas usando a definição existente.</span><span class="sxs-lookup"><span data-stu-id="8d09a-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="8d09a-105">Este tópico fornece uma visão geral da execução lado a lado do serviço de fluxo de trabalho usando <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d09a-106">Para baixar um exemplo e assistir uma vídeo passo a passo do controle de versão de lado a lado do serviço de fluxo de trabalho, consulte [controle de versão lado a lado com um serviço de fluxo de trabalho Xamlx hospedado na Web](https://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="8d09a-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](https://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="8d09a-107">Hospedando várias versões em um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d09a-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="8d09a-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contém duas propriedades que podem ser configuradas para permitir que várias versões de um fluxo de trabalho sejam executadas lado a lado: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> e <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="8d09a-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contém as versões suportadas do serviço de fluxo de trabalho, e <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> é usado para identificar exclusivamente cada serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8d09a-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="8d09a-110">Isso é feito por meio da associação de um <xref:System.Activities.WorkflowIdentity> com o serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8d09a-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="8d09a-111">Uma instância <xref:System.Activities.WorkflowIdentity> contém três informações de identificação.</span><span class="sxs-lookup"><span data-stu-id="8d09a-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="8d09a-112"><xref:System.Activities.WorkflowIdentity.Name%2A> e <xref:System.Activities.WorkflowIdentity.Version%2A> contêm um nome e um <xref:System.Version> e são necessários, e <xref:System.Activities.WorkflowIdentity.Package%2A> é opcional e pode ser usado para especificar uma cadeia de caracteres adicional que contém informações como o nome do assembly ou outras informações desejadas.</span><span class="sxs-lookup"><span data-stu-id="8d09a-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="8d09a-113">Cada serviço de fluxo de trabalho contido na coleção <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> deve ter um único <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="8d09a-114">Um <xref:System.Activities.WorkflowIdentity> é exclusivo se qualquer uma de suas três propriedades for diferente da outra <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="8d09a-115">Um `null` <xref:System.Activities.WorkflowIdentity> é um valor permitido para <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, mas apenas uma versão anterior de um serviço de fluxo de trabalho pode ter um `null` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d09a-116">Um <xref:System.Activities.WorkflowIdentity> não deve conter informações pessoalmente identificáveis (PII).</span><span class="sxs-lookup"><span data-stu-id="8d09a-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="8d09a-117"><xref:System.Activities.WorkflowIdentity> é composto por três partes : um <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), um <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) e um <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="8d09a-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="8d09a-118">As informações sobre o <xref:System.Activities.WorkflowIdentity> usadas para criar uma instância são emitidas para todos os serviços de rastreamento configurados em vários pontos diferentes do ciclo de vida da atividade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8d09a-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="8d09a-119">O Rastreamento WF não tem nenhum mecanismo para ocultar o PII (dados de usuário confidenciais).</span><span class="sxs-lookup"><span data-stu-id="8d09a-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="8d09a-120">Portanto, uma instância <xref:System.Activities.WorkflowIdentity> não deve conter nenhum dado de PII porque será emitido pelo tempo de execução em registros de rastreamento e pode estar visível para qualquer um com acesso para exibir os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="8d09a-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="8d09a-121">Regras para hospedar várias versões de um serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8d09a-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="8d09a-122">Quando um usuário adiciona uma versão adicional ao <xref:System.ServiceModel.Activities.WorkflowServiceHost>, há várias condições que devem ser cumpridas para que um serviço de fluxo de trabalho seja hospedado com o mesmo conjunto de pontos de extremidade e uma descrição.</span><span class="sxs-lookup"><span data-stu-id="8d09a-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="8d09a-123">Se qualquer uma das versões adicionais não atenderem a essas condições, o <xref:System.ServiceModel.Activities.WorkflowServiceHost> gera uma exceção quando `Open` é chamado.</span><span class="sxs-lookup"><span data-stu-id="8d09a-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="8d09a-124">Cada definição de fluxo de trabalho fornecida para o host como uma versão adicional deve atender aos seguintes requisitos (onde a versão principal é a definição do serviço de fluxo de trabalho é fornecida para o construtor de host).</span><span class="sxs-lookup"><span data-stu-id="8d09a-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="8d09a-125">A versão de fluxo de trabalho adicional deverá:</span><span class="sxs-lookup"><span data-stu-id="8d09a-125">The additional workflow version must:</span></span>  
  
- <span data-ttu-id="8d09a-126">Ter o mesmo <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> que a versão principal do serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8d09a-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
- <span data-ttu-id="8d09a-127">Não deve ter quaisquer atividades <xref:System.ServiceModel.Activities.Receive> ou <xref:System.ServiceModel.Activities.SendReply> no seu <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> que não são da versão principal, e eles devem corresponder ao contrato de operação.</span><span class="sxs-lookup"><span data-stu-id="8d09a-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
- <span data-ttu-id="8d09a-128">Ter um único <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="8d09a-129">Somente uma definição de fluxo de trabalho pode ter um `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="8d09a-130">Algumas alterações são permitidas.</span><span class="sxs-lookup"><span data-stu-id="8d09a-130">Some changes are permitted.</span></span> <span data-ttu-id="8d09a-131">Os itens a seguir podem ser diferentes entre as versões:</span><span class="sxs-lookup"><span data-stu-id="8d09a-131">The following items may be different between the versions:</span></span>  
  
- <span data-ttu-id="8d09a-132">O <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> pode ter um nome e um pacote diferente que a versão principal.</span><span class="sxs-lookup"><span data-stu-id="8d09a-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
- <span data-ttu-id="8d09a-133">O valor <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> pode ser diferente da versão principal.</span><span class="sxs-lookup"><span data-stu-id="8d09a-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
- <span data-ttu-id="8d09a-134">O <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> pode ser diferente da versão principal.</span><span class="sxs-lookup"><span data-stu-id="8d09a-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
- <span data-ttu-id="8d09a-135">O <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> pode ser diferente da versão principal.</span><span class="sxs-lookup"><span data-stu-id="8d09a-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="8d09a-136">Configurando a DefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8d09a-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="8d09a-137">Quando um serviço de fluxo de trabalho é criado usando o designer de fluxo de trabalho, o <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> é definido usando o **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="8d09a-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="8d09a-138">Clique fora da atividade de raiz do serviço no designer para selecionar o serviço de fluxo de trabalho e, em seguida, escolha **janela de propriedades** da **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="8d09a-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="8d09a-139">Selecione **WorkflowIdentity** na lista suspensa que aparece ao lado de **DefinitionIdentity** propriedade e, em seguida, expanda e especifique os detalhes desejados <xref:System.Activities.WorkflowIdentity> propriedades.</span><span class="sxs-lookup"><span data-stu-id="8d09a-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="8d09a-140">No exemplo a seguir a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> está configurado com o <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` e uma <xref:System.Activities.WorkflowIdentity.Version%2A> de `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="8d09a-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="8d09a-141"><xref:System.Activities.WorkflowIdentity.Package%2A> é opcional e neste exemplo é `null`.</span><span class="sxs-lookup"><span data-stu-id="8d09a-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 ![Captura de tela que mostra a propriedade DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 <span data-ttu-id="8d09a-143">Quando um serviço de fluxo de trabalho é auto-hospedado, o <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> é configurado quando o serviço de fluxo de trabalho é criado.</span><span class="sxs-lookup"><span data-stu-id="8d09a-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="8d09a-144">No exemplo a seguir, o <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> está configurado com os mesmos valores do exemplo anterior, com o <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` e uma <xref:System.Activities.WorkflowIdentity.Name%2A> de `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="8d09a-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 <span data-ttu-id="8d09a-145">Um <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> não é obrigatório, embora apenas uma versão do serviço de fluxo de trabalho pode ter um **nulo**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d09a-146">Isso é útil se o serviço foi implantado inicialmente sem um <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configurado, e uma versão atualizada é criada.</span><span class="sxs-lookup"><span data-stu-id="8d09a-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="8d09a-147">Adicionar uma nova versão a um serviço de fluxo de trabalho hospedado na web</span><span class="sxs-lookup"><span data-stu-id="8d09a-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="8d09a-148">A primeira etapa na configuração de uma nova versão de um serviço de fluxo de trabalho em um serviço hospedado na web é criar uma nova pasta na pasta `App_Code` com o mesmo nome do arquivo de serviço.</span><span class="sxs-lookup"><span data-stu-id="8d09a-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="8d09a-149">Se arquivo `xamlx` do serviço é chamado de `MortgageWorkflow.xamlx`, a pasta deve ser nomeada como `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="8d09a-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="8d09a-150">Coloque uma cópia do arquivo `xamlx` original do serviço nesta pasta e renomeie-o para um novo nome, como `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="8d09a-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="8d09a-151">Faça as alterações desejadas no serviço primário, atualize seu <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> e implante o serviço.</span><span class="sxs-lookup"><span data-stu-id="8d09a-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="8d09a-152">No exemplo a seguir, o <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> foi atualizado com um <xref:System.Activities.WorkflowIdentity.Name%2A> de `MortgageWorkflow` e um <xref:System.Activities.WorkflowIdentity.Version%2A> de `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="8d09a-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 ![Captura de tela que mostra a DefinitionIdentity da WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 <span data-ttu-id="8d09a-154">Quando o serviço for reiniciado, a versão anterior será automaticamente adicionada à coleção <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>, porque ela está localizada na subpasta `App_Code` designada.</span><span class="sxs-lookup"><span data-stu-id="8d09a-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="8d09a-155">Observe que, se a versão principal do serviço de fluxo de trabalho tem um `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> as versões anteriores não serão adicionadas.</span><span class="sxs-lookup"><span data-stu-id="8d09a-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="8d09a-156">Uma versão pode ter um `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, mas se houver várias versões, a versão principal não deve ser aquela com o `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, senão as versões anteriores não serão adicionadas à coleção <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="8d09a-157">Adicionar uma nova versão a um serviço de fluxo de trabalho auto-hospedado</span><span class="sxs-lookup"><span data-stu-id="8d09a-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="8d09a-158">Ao adicionar uma nova versão a um serviço de fluxo de trabalho auto-hospedado, o <xref:System.ServiceModel.Activities.WorkflowServiceHost> é configurado com a versão principal do serviço de fluxo de trabalho, e as versões anteriores devem ser adicionadas explicitamente à coleção <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="8d09a-159">No exemplo a seguir, um <xref:System.ServiceModel.Activities.WorkflowServiceHost> é configurado com um serviço de fluxo de trabalho principal que usa uma definição de fluxo de trabalho `MortgageWorkflowV2` e um serviço de fluxo de trabalho configurado com uma definição de fluxo de trabalho `MortgageWorkflowV1` é adicionado à coleção <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d09a-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="8d09a-160">Cada serviço de fluxo de trabalho é configurado com um único <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> que reflete a versão da definição de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8d09a-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,   
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
