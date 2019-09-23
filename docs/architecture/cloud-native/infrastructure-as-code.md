---
title: Infraestrutura como código
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Infraestrutura como código
ms.date: 06/30/2019
ms.openlocfilehash: e395db28bdeff785251b91ed643f9920873d26e8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183010"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="9cd42-103">Infraestrutura como código</span><span class="sxs-lookup"><span data-stu-id="9cd42-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9cd42-104">Os aplicativos nativos de nuvem tendem a fazer uso de todos os tipos de componentes de PaaS (plataforma como serviço) fantásticos.</span><span class="sxs-lookup"><span data-stu-id="9cd42-104">Cloud-native applications tend to make use of all sorts of fantastic platform as a service (PaaS) components.</span></span> <span data-ttu-id="9cd42-105">Em uma plataforma de nuvem como o Azure, esses componentes podem incluir itens como armazenamento, barramento de serviço e o serviço Signalr.</span><span class="sxs-lookup"><span data-stu-id="9cd42-105">On a cloud platform like Azure, these components might include things like storage, Service Bus, and the SignalR service.</span></span> <span data-ttu-id="9cd42-106">À medida que os aplicativos se tornam mais complicados, o número desses serviços em uso provavelmente aumentará.</span><span class="sxs-lookup"><span data-stu-id="9cd42-106">As applications become more complicated, the number of these services in use is likely to grow.</span></span> <span data-ttu-id="9cd42-107">Assim como a entrega contínua quebrou o modelo tradicional de implantação em um ambiente manualmente, o ritmo rápido de alteração também quebrou o modelo de ter um grupo de ti centralizado gerenciar ambientes.</span><span class="sxs-lookup"><span data-stu-id="9cd42-107">Just as how continuous delivery broke the traditional model of deploying to an environment manually, the rapid pace of change also broke the model of having a centralized IT group manage environments.</span></span>

<span data-ttu-id="9cd42-108">A criação de ambientes pode, e também ser automatizada.</span><span class="sxs-lookup"><span data-stu-id="9cd42-108">Building environments can, and should, also be automated.</span></span> <span data-ttu-id="9cd42-109">Há uma ampla variedade de ferramentas bem pensadas que podem facilitar o processo.</span><span class="sxs-lookup"><span data-stu-id="9cd42-109">There's a wide range of well thought out tools that can make the process easy.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="9cd42-110">Modelos de Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="9cd42-110">Azure Resource Manager templates</span></span>

<span data-ttu-id="9cd42-111">Os modelos de Azure Resource Manager são uma linguagem baseada em JSON para definir vários recursos no Azure.</span><span class="sxs-lookup"><span data-stu-id="9cd42-111">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="9cd42-112">O esquema básico é semelhante a Figura 11-10.</span><span class="sxs-lookup"><span data-stu-id="9cd42-112">The basic schema looks something like Figure 11-10.</span></span>

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "",
  "apiProfile": "",
  "parameters": {  },
  "variables": {  },
  "functions": [  ],
  "resources": [  ],
  "outputs": {  }
}
```

<span data-ttu-id="9cd42-113">**Figura 11-10** -o esquema para um modelo do Resource Manager</span><span class="sxs-lookup"><span data-stu-id="9cd42-113">**Figure 11-10** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="9cd42-114">Nesse modelo, é possível definir um contêiner de armazenamento dentro da seção de recursos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9cd42-114">Within this template, one might define a storage container inside the resources section like so:</span></span>
 
```json
"resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "[variables('storageAccountName')]",
      "location": "[parameters('location')]",
      "apiVersion": "2018-07-01",
      "sku": {
        "name": "[parameters('storageAccountType')]"
      },
      "kind": "StorageV2",
      "properties": {}
    }
  ],
```

<span data-ttu-id="9cd42-115">**Figura 11-11** -um exemplo de uma conta de armazenamento definida em um modelo do Resource Manager</span><span class="sxs-lookup"><span data-stu-id="9cd42-115">**Figure 11-11** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="9cd42-116">Os modelos podem ser parametrizados para que um modelo possa ser reutilizado com configurações diferentes para definir ambientes de desenvolvimento, QA e produção.</span><span class="sxs-lookup"><span data-stu-id="9cd42-116">The templates can be parameterized so that one template can be reused with different settings to define development, QA, and production environments.</span></span> <span data-ttu-id="9cd42-117">Isso ajuda a eliminar surpresas ao migrar para um ambiente superior configurado de forma diferente dos ambientes inferiores.</span><span class="sxs-lookup"><span data-stu-id="9cd42-117">This helps eliminate surprises when migrating to a higher environment that is set up differently from the lower environments.</span></span> <span data-ttu-id="9cd42-118">Os recursos definidos em um modelo normalmente são todos criados dentro de um único grupo de recursos no Azure (é possível definir vários grupos de recursos em um único modelo do Resource Manager, mas incomum).</span><span class="sxs-lookup"><span data-stu-id="9cd42-118">The resources defined in a template are typically all created within a single resource group on Azure (it's possible to define multiple resource groups in a single Resource Manager template but unusual).</span></span> <span data-ttu-id="9cd42-119">Isso torna muito fácil excluir um ambiente apenas excluindo o grupo de recursos como um todo.</span><span class="sxs-lookup"><span data-stu-id="9cd42-119">This makes it very easy to delete an environment by just deleting the resource group as a whole.</span></span> <span data-ttu-id="9cd42-120">A análise de custo também pode ser executada no nível do grupo de recursos, permitindo uma rápida contabilidade de quanto cada ambiente está custando.</span><span class="sxs-lookup"><span data-stu-id="9cd42-120">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="9cd42-121">Há muitos modelos de exemplo definidos no projeto de [modelos de início rápido do Azure](https://github.com/Azure/azure-quickstart-templates) no GitHub que darão um trecho ao iniciar em um novo modelo ou a adicionar a um existente.</span><span class="sxs-lookup"><span data-stu-id="9cd42-121">There are many example templates defined in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub that will give a leg up when starting on a new template or adding to an existing one.</span></span>

<span data-ttu-id="9cd42-122">Os modelos do Resource Manager podem ser executados de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="9cd42-122">Resource Manager templates can be run in a variety of ways.</span></span> <span data-ttu-id="9cd42-123">Talvez a maneira mais simples seja simplesmente colá-las no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="9cd42-123">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="9cd42-124">Para implantações experimentais, esse método pode ser muito rápido.</span><span class="sxs-lookup"><span data-stu-id="9cd42-124">For experimental deployments, this method can be very quick.</span></span> <span data-ttu-id="9cd42-125">Eles também podem ser executados como parte de um processo de compilação ou versão no Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="9cd42-125">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="9cd42-126">Há tarefas que usarão conexões no Azure para executar os modelos.</span><span class="sxs-lookup"><span data-stu-id="9cd42-126">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="9cd42-127">As alterações nos modelos do Resource Manager são aplicadas incrementalmente, o que significa que, para adicionar um novo recurso, é necessário apenas adicioná-lo ao modelo.</span><span class="sxs-lookup"><span data-stu-id="9cd42-127">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="9cd42-128">As ferramentas tratarão de diferenciar o grupo de recursos atual com o grupo de recursos desejado definido no modelo.</span><span class="sxs-lookup"><span data-stu-id="9cd42-128">The tooling will handle diffing the current resource group with the desired resource group defined in the template.</span></span> <span data-ttu-id="9cd42-129">Os recursos serão criados ou alterados para que correspondam ao que está definido no modelo.</span><span class="sxs-lookup"><span data-stu-id="9cd42-129">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="9cd42-130">Terraform</span><span class="sxs-lookup"><span data-stu-id="9cd42-130">Terraform</span></span>

<span data-ttu-id="9cd42-131">Uma desvantagem percebida dos modelos do Resource Manager é que eles são específicos para a nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="9cd42-131">A perceived disadvantage of Resource Manager templates is that they are specific to the Azure cloud.</span></span> <span data-ttu-id="9cd42-132">É incomum criar aplicativos que incluem recursos de mais de uma nuvem, mas nos casos em que a empresa depende de tempo de atividade espetacular, o custo de dar suporte a várias nuvens pode ser válido.</span><span class="sxs-lookup"><span data-stu-id="9cd42-132">It's unusual to create applications that include resources from more than one cloud, but in cases where the business relies on spectacular uptime, the cost of supporting multiple clouds might be worthwhile.</span></span> <span data-ttu-id="9cd42-133">Se houvesse uma linguagem de modelagem que pudesse ser usada em cada nuvem, ela também permitiria que as habilidades do desenvolvedor fossem muito mais portáveis.</span><span class="sxs-lookup"><span data-stu-id="9cd42-133">If there were one templating language that could be used across every cloud, then it would also allow for developer skills to be much more portable.</span></span>

<span data-ttu-id="9cd42-134">Existem várias tecnologias que fazem exatamente isso!</span><span class="sxs-lookup"><span data-stu-id="9cd42-134">Several technologies exist which do just that!</span></span> <span data-ttu-id="9cd42-135">A oferta mais madura nesse espaço é conhecida como [Terraform](https://www.terraform.io/).</span><span class="sxs-lookup"><span data-stu-id="9cd42-135">The most mature offering in that space is known as [Terraform](https://www.terraform.io/).</span></span> <span data-ttu-id="9cd42-136">O Terraform dá suporte a todos os principais players de nuvem, como o Azure, Google Cloud Platform, AWS e o, além de dar suporte a dezenas de jogadores secundários, como Heroku e DigitalOcean.</span><span class="sxs-lookup"><span data-stu-id="9cd42-136">Terraform supports every major cloud player such as Azure, Google Cloud Platform, AWS, and AliCloud, and it also supports dozens of minor players such as Heroku and DigitalOcean.</span></span> <span data-ttu-id="9cd42-137">Em vez de usar JSON como a linguagem de definição de modelo, ele usa o YAML ligeiramente mais conciso.</span><span class="sxs-lookup"><span data-stu-id="9cd42-137">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span> 

<span data-ttu-id="9cd42-138">Um arquivo Terraform de exemplo que faz o mesmo que o modelo do Resource Manager anterior (Figura 11-11) é mostrado na Figura 11-12:</span><span class="sxs-lookup"><span data-stu-id="9cd42-138">An example Terraform file that does the same as the previous Resource Manager template (Figure 11-11) is shown in Figure 11-12:</span></span>

```terraform
provider "azurerm" {
  version = "=1.28.0"
}

resource "azurerm_resource_group" "test" {
  name     = "production"
  location = "West US"
}

resource "azurerm_storage_account" "testsa" {
  name                     = "${var.storageAccountName}"
  resource_group_name      = "${azurerm_resource_group.testrg.name}"
  location                 = "${var.region}"
  account_tier             = "${var.tier}"
  account_replication_type = "${var.replicationType}"

}
```

<span data-ttu-id="9cd42-139">**Figura 11-12** -um exemplo de um modelo do Resource Manager</span><span class="sxs-lookup"><span data-stu-id="9cd42-139">**Figure 11-12** - An example of a Resource Manager template</span></span>

<span data-ttu-id="9cd42-140">O Terraform faz um trabalho melhor de fornecer mensagens de erro sensatas quando um recurso não pode ser implantado devido a um erro no modelo.</span><span class="sxs-lookup"><span data-stu-id="9cd42-140">Terraform does a better job of providing sensible error messages when a resource can't be deployed because of an error in the template.</span></span> <span data-ttu-id="9cd42-141">Essa é uma área em que os modelos do Resource Manager têm alguns desafios contínuos.</span><span class="sxs-lookup"><span data-stu-id="9cd42-141">This is an area where Resource Manager templates have some ongoing challenges.</span></span> <span data-ttu-id="9cd42-142">Também há uma tarefa de validação muito útil que pode ser usada na fase de compilação para detectar erros de modelo no início.</span><span class="sxs-lookup"><span data-stu-id="9cd42-142">There's also a very handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="9cd42-143">Assim como acontece com os modelos do Resource Manager, há ferramentas de linha de comando que podem ser usadas para implantar modelos Terraform.</span><span class="sxs-lookup"><span data-stu-id="9cd42-143">As with Resource Manager templates, there are command-line tools that can be used to deploy Terraform templates.</span></span> <span data-ttu-id="9cd42-144">Também há tarefas criadas pela Comunidade no Azure Pipelines que podem validar e aplicar modelos Terraform.</span><span class="sxs-lookup"><span data-stu-id="9cd42-144">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="9cd42-145">Caso o modelo do Terraform ou do Resource Manager gere valores interessantes, como a cadeia de conexão para um banco de dados recém-criado, eles podem ser capturados no pipeline de compilação e usados em tarefas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="9cd42-145">In the event that the Terraform or Resource Manager template outputs interesting values such as the connection string to a newly created database they can be captured in the build pipeline and used in subsequent tasks.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9cd42-146">[Anterior](devops.md)
>[Próximo](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="9cd42-146">[Previous](devops.md)
[Next](application-bundles.md)</span></span>
