---
title: Infraestrutura como código
description: Adotando a infraestrutura como código (IaC) com aplicativos nativos de nuvem
ms.date: 05/12/2020
ms.openlocfilehash: 309dd8610ab3b72a6c6da5297f109f822520c5ff
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395342"
---
# <a name="infrastructure-as-code"></a><span data-ttu-id="d0d62-103">Infraestrutura como código</span><span class="sxs-lookup"><span data-stu-id="d0d62-103">Infrastructure as code</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d0d62-104">Os sistemas nativos de nuvem adotam microserviços, contêineres e design de sistema moderno para atingir velocidade e agilidade.</span><span class="sxs-lookup"><span data-stu-id="d0d62-104">Cloud-native systems embrace microservices, containers, and modern system design to achieve speed and agility.</span></span> <span data-ttu-id="d0d62-105">Eles fornecem estágios automatizados de Build e versão para garantir o código consistente e de qualidade.</span><span class="sxs-lookup"><span data-stu-id="d0d62-105">They provide automated build and release stages to ensure consistent and quality code.</span></span> <span data-ttu-id="d0d62-106">Mas isso é apenas parte da história.</span><span class="sxs-lookup"><span data-stu-id="d0d62-106">But, that's only part of the story.</span></span> <span data-ttu-id="d0d62-107">Como provisionar os ambientes de nuvem nos quais esses sistemas são executados?</span><span class="sxs-lookup"><span data-stu-id="d0d62-107">How do you provision the cloud environments upon which these systems run?</span></span>

<span data-ttu-id="d0d62-108">Os aplicativos nativos de nuvem modernos adotam a prática amplamente aceita da [Infraestrutura como código](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)ou `IaC` .</span><span class="sxs-lookup"><span data-stu-id="d0d62-108">Modern cloud-native applications embrace the widely accepted practice of [Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), or `IaC`.</span></span>  <span data-ttu-id="d0d62-109">Com o IaC, você automatiza o provisionamento de plataforma.</span><span class="sxs-lookup"><span data-stu-id="d0d62-109">With IaC, you automate platform provisioning.</span></span> <span data-ttu-id="d0d62-110">Essencialmente, você aplica práticas de engenharia de software, como teste e controle de versão, às suas práticas de DevOps.</span><span class="sxs-lookup"><span data-stu-id="d0d62-110">You essentially apply software engineering practices such as testing and versioning to your DevOps practices.</span></span> <span data-ttu-id="d0d62-111">Sua infraestrutura e implantações são automatizadas, consistentes e reproduzíveis.</span><span class="sxs-lookup"><span data-stu-id="d0d62-111">Your infrastructure and deployments are automated, consistent, and repeatable.</span></span> <span data-ttu-id="d0d62-112">Assim como a entrega contínua automatizada do modelo tradicional de implantações manuais, a infraestrutura como código (IaC) está evoluindo como os ambientes de aplicativos são gerenciados.</span><span class="sxs-lookup"><span data-stu-id="d0d62-112">Just as continuous delivery automated the traditional model of manual deployments, Infrastructure as Code (IaC) is evolving how application environments are managed.</span></span>

<span data-ttu-id="d0d62-113">Ferramentas como Azure Resource Manager (ARM), Terraform e a CLI (interface de linha de comando) do Azure permitem gerar um script de forma declarativa para a infraestrutura de nuvem necessária.</span><span class="sxs-lookup"><span data-stu-id="d0d62-113">Tools like Azure Resource Manager (ARM), Terraform, and the Azure Command Line Interface (CLI) enable you to declaratively script the cloud infrastructure you require.</span></span>

## <a name="azure-resource-manager-templates"></a><span data-ttu-id="d0d62-114">Modelos do Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="d0d62-114">Azure Resource Manager templates</span></span>

<span data-ttu-id="d0d62-115">ARM significa [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span><span class="sxs-lookup"><span data-stu-id="d0d62-115">ARM stands for [Azure Resource Manager](https://azure.microsoft.com/documentation/articles/resource-group-overview/).</span></span> <span data-ttu-id="d0d62-116">É um mecanismo de provisionamento de API que é incorporado ao Azure e exposto como um serviço de API.</span><span class="sxs-lookup"><span data-stu-id="d0d62-116">It's an API provisioning engine that is built into Azure and exposed as an API service.</span></span> <span data-ttu-id="d0d62-117">O ARM permite que você implante, atualize, exclua e gerencie os recursos contidos no grupo de recursos do Azure em uma única operação coordenada.</span><span class="sxs-lookup"><span data-stu-id="d0d62-117">ARM enables you to deploy, update, delete, and manage the resources contained in Azure resource group in a single, coordinated operation.</span></span> <span data-ttu-id="d0d62-118">Você fornece ao mecanismo um modelo baseado em JSON que especifica os recursos necessários e sua configuração.</span><span class="sxs-lookup"><span data-stu-id="d0d62-118">You provide the engine with a JSON-based template that specifies the resources you require and their configuration.</span></span> <span data-ttu-id="d0d62-119">O ARM orquestra automaticamente a implantação na ordem correta que respeita as dependências.</span><span class="sxs-lookup"><span data-stu-id="d0d62-119">ARM automatically orchestrates the deployment in the correct order respecting dependencies.</span></span> <span data-ttu-id="d0d62-120">O mecanismo garante Idempotência.</span><span class="sxs-lookup"><span data-stu-id="d0d62-120">The engine ensures idempotency.</span></span> <span data-ttu-id="d0d62-121">Se um recurso desejado já existir com a mesma configuração, o provisionamento será ignorado.</span><span class="sxs-lookup"><span data-stu-id="d0d62-121">If a desired resource already exists with the same configuration, provisioning will be ignored.</span></span>

<span data-ttu-id="d0d62-122">Os modelos de Azure Resource Manager são uma linguagem baseada em JSON para definir vários recursos no Azure.</span><span class="sxs-lookup"><span data-stu-id="d0d62-122">Azure Resource Manager templates are a JSON-based language for defining various resources in Azure.</span></span> <span data-ttu-id="d0d62-123">O esquema básico é semelhante a Figura 10-14.</span><span class="sxs-lookup"><span data-stu-id="d0d62-123">The basic schema looks something like Figure 10-14.</span></span>

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

<span data-ttu-id="d0d62-124">**Figura 10-14** -o esquema para um modelo do Resource Manager</span><span class="sxs-lookup"><span data-stu-id="d0d62-124">**Figure 10-14** - The schema for a Resource Manager template</span></span>

<span data-ttu-id="d0d62-125">Nesse modelo, é possível definir um contêiner de armazenamento dentro da seção de recursos da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d0d62-125">Within this template, one might define a storage container inside the resources section like so:</span></span>

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

<span data-ttu-id="d0d62-126">**Figura 10-15** -um exemplo de uma conta de armazenamento definida em um modelo do Resource Manager</span><span class="sxs-lookup"><span data-stu-id="d0d62-126">**Figure 10-15** - An example of a storage account defined in a Resource Manager template</span></span>

<span data-ttu-id="d0d62-127">Um modelo de ARM pode ser parametrizado com informações de ambiente dinâmico e configuração.</span><span class="sxs-lookup"><span data-stu-id="d0d62-127">An ARM template can be parameterized with dynamic environment and configuration information.</span></span> <span data-ttu-id="d0d62-128">Isso permite que ele seja reutilizado para definir ambientes diferentes, como desenvolvimento, p e r ou produção.</span><span class="sxs-lookup"><span data-stu-id="d0d62-128">Doing so enables it to be reused to define different environments, such as development, QA, or production.</span></span> <span data-ttu-id="d0d62-129">Normalmente, o modelo cria todos os recursos em um único grupo de recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="d0d62-129">Normally, the template creates all resources within a single Azure resource group.</span></span> <span data-ttu-id="d0d62-130">É possível definir vários grupos de recursos em um único modelo do Resource Manager, se necessário.</span><span class="sxs-lookup"><span data-stu-id="d0d62-130">It's possible to define multiple resource groups in a single Resource Manager template, if needed.</span></span> <span data-ttu-id="d0d62-131">Você pode excluir todos os recursos em um ambiente excluindo o próprio grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="d0d62-131">You can delete all resources in an environment by deleting the resource group itself.</span></span> <span data-ttu-id="d0d62-132">A análise de custo também pode ser executada no nível do grupo de recursos, permitindo uma rápida contabilidade de quanto cada ambiente está custando.</span><span class="sxs-lookup"><span data-stu-id="d0d62-132">Cost analysis can also be run at the resource group level, allowing for quick accounting of how much each environment is costing.</span></span>

<span data-ttu-id="d0d62-133">Há muitos exemplos ou modelos de ARM disponíveis no projeto de [modelos de início rápido do Azure](https://github.com/Azure/azure-quickstart-templates) no github.</span><span class="sxs-lookup"><span data-stu-id="d0d62-133">There are many examples or ARM templates available in the [Azure Quickstart Templates](https://github.com/Azure/azure-quickstart-templates) project on GitHub.</span></span> <span data-ttu-id="d0d62-134">Eles podem ajudar a acelerar a criação de um novo modelo ou a modificação de um existente.</span><span class="sxs-lookup"><span data-stu-id="d0d62-134">They can help accelerate creating a new template or modifying an existing one.</span></span>

<span data-ttu-id="d0d62-135">Os modelos do Resource Manager podem ser executados de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="d0d62-135">Resource Manager templates can be run in many of ways.</span></span> <span data-ttu-id="d0d62-136">Talvez a maneira mais simples seja simplesmente colá-las no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="d0d62-136">Perhaps the simplest way is to simply paste them into the Azure portal.</span></span> <span data-ttu-id="d0d62-137">Para implantações experimentais, esse método pode ser rápido.</span><span class="sxs-lookup"><span data-stu-id="d0d62-137">For experimental deployments, this method can be quick.</span></span> <span data-ttu-id="d0d62-138">Eles também podem ser executados como parte de um processo de compilação ou versão no Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="d0d62-138">They can also be run as part of a build or release process in Azure DevOps.</span></span> <span data-ttu-id="d0d62-139">Há tarefas que usarão conexões no Azure para executar os modelos.</span><span class="sxs-lookup"><span data-stu-id="d0d62-139">There are tasks that will leverage connections into Azure to run the templates.</span></span> <span data-ttu-id="d0d62-140">As alterações nos modelos do Resource Manager são aplicadas incrementalmente, o que significa que, para adicionar um novo recurso, é necessário apenas adicioná-lo ao modelo.</span><span class="sxs-lookup"><span data-stu-id="d0d62-140">Changes to Resource Manager templates are applied incrementally, meaning that to add a new resource requires just adding it to the template.</span></span> <span data-ttu-id="d0d62-141">As ferramentas irão reconciliar as diferenças entre os recursos atuais e os definidos no modelo.</span><span class="sxs-lookup"><span data-stu-id="d0d62-141">The tooling will reconcile differences between the current resources and those defined in the template.</span></span> <span data-ttu-id="d0d62-142">Os recursos serão criados ou alterados para que correspondam ao que está definido no modelo.</span><span class="sxs-lookup"><span data-stu-id="d0d62-142">Resources will then be created or altered so they match what is defined in the template.</span></span>  

## <a name="terraform"></a><span data-ttu-id="d0d62-143">Terraform</span><span class="sxs-lookup"><span data-stu-id="d0d62-143">Terraform</span></span>

<span data-ttu-id="d0d62-144">Em geral, os aplicativos nativos da nuvem são construídos `cloud agnostic` .</span><span class="sxs-lookup"><span data-stu-id="d0d62-144">Cloud-native applications are often constructed to be `cloud agnostic`.</span></span> <span data-ttu-id="d0d62-145">Sendo assim, isso significa que o aplicativo não está rigidamente acoplado a um fornecedor de nuvem específico e pode ser implantado em qualquer nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="d0d62-145">Being so means the application isn't tightly coupled to a particular cloud vendor and can be deployed to any public cloud.</span></span>

<span data-ttu-id="d0d62-146">O [Terraform](https://www.terraform.io/) é uma ferramenta de modelagem de negócios que pode provisionar aplicativos nativos de nuvem em todos os principais players de nuvem: Azure, Google Cloud Platform, AWS e o antiicloud.</span><span class="sxs-lookup"><span data-stu-id="d0d62-146">[Terraform](https://www.terraform.io/) is commercial templating tool that can provision cloud-native applications across all the major cloud players: Azure, Google Cloud Platform, AWS, and AliCloud.</span></span> <span data-ttu-id="d0d62-147">Em vez de usar JSON como a linguagem de definição de modelo, ele usa o YAML ligeiramente mais conciso.</span><span class="sxs-lookup"><span data-stu-id="d0d62-147">Instead of using JSON as the template definition language, it uses the slightly more terse YAML.</span></span>

<span data-ttu-id="d0d62-148">Um arquivo Terraform de exemplo que faz o mesmo que o modelo do Resource Manager anterior (Figura 10-15) é mostrado na Figura 10-16:</span><span class="sxs-lookup"><span data-stu-id="d0d62-148">An example Terraform file that does the same as the previous Resource Manager template (Figure 10-15) is shown in Figure 10-16:</span></span>

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

<span data-ttu-id="d0d62-149">**Figura 10-16** -um exemplo de um modelo do Resource Manager</span><span class="sxs-lookup"><span data-stu-id="d0d62-149">**Figure 10-16** - An example of a Resource Manager template</span></span>

<span data-ttu-id="d0d62-150">O Terraform também fornece mensagens de erro intuitivas para modelos de problemas.</span><span class="sxs-lookup"><span data-stu-id="d0d62-150">Terraform also provides intuitive error messages for problem templates.</span></span> <span data-ttu-id="d0d62-151">Também há uma tarefa de validação prática que pode ser usada na fase de compilação para detectar erros de modelo no início.</span><span class="sxs-lookup"><span data-stu-id="d0d62-151">There's also a handy validate task that can be used in the build phase to catch template errors early.</span></span>

<span data-ttu-id="d0d62-152">Assim como acontece com os modelos do Resource Manager, as ferramentas de linha de comando estão disponíveis para implantar modelos Terraform.</span><span class="sxs-lookup"><span data-stu-id="d0d62-152">As with Resource Manager templates, command-line tools are available to deploy Terraform templates.</span></span> <span data-ttu-id="d0d62-153">Também há tarefas criadas pela Comunidade no Azure Pipelines que podem validar e aplicar modelos Terraform.</span><span class="sxs-lookup"><span data-stu-id="d0d62-153">There are also community-created tasks in Azure Pipelines that can validate and apply Terraform templates.</span></span>

<span data-ttu-id="d0d62-154">Às vezes, os modelos Terraform e ARM geram valores significativos, como uma cadeia de conexão para um banco de dados recém-criado.</span><span class="sxs-lookup"><span data-stu-id="d0d62-154">Sometimes Terraform and ARM templates output meaningful values, such as a connection string to a newly created database.</span></span> <span data-ttu-id="d0d62-155">Essas informações podem ser capturadas no pipeline de compilação e usadas em tarefas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="d0d62-155">This information can be captured in the build pipeline and used in subsequent tasks.</span></span>

## <a name="azure-cli-scripts-and-tasks"></a><span data-ttu-id="d0d62-156">CLI do Azure scripts e tarefas</span><span class="sxs-lookup"><span data-stu-id="d0d62-156">Azure CLI Scripts and Tasks</span></span>

<span data-ttu-id="d0d62-157">Por fim, você pode aproveitar [CLI do Azure](https://docs.microsoft.com/cli/azure/) para gerar um script declarativa de sua infraestrutura de nuvem.</span><span class="sxs-lookup"><span data-stu-id="d0d62-157">Finally, you can leverage [Azure CLI](https://docs.microsoft.com/cli/azure/) to declaratively script your cloud infrastructure.</span></span> <span data-ttu-id="d0d62-158">CLI do Azure scripts podem ser criados, encontrados e compartilhados para provisionar e configurar quase todos os recursos do Azure.</span><span class="sxs-lookup"><span data-stu-id="d0d62-158">Azure CLI scripts can be created, found, and shared to provision and configure almost any Azure resource.</span></span> <span data-ttu-id="d0d62-159">A CLI é simples de usar com uma curva de aprendizado de AdaBoost.</span><span class="sxs-lookup"><span data-stu-id="d0d62-159">The CLI is simple to use with a gentle learning curve.</span></span> <span data-ttu-id="d0d62-160">Os scripts são executados no PowerShell ou bash.</span><span class="sxs-lookup"><span data-stu-id="d0d62-160">Scripts are executed within either PowerShell or Bash.</span></span> <span data-ttu-id="d0d62-161">Eles também são simples de depurar, especialmente quando comparados com modelos ARM.</span><span class="sxs-lookup"><span data-stu-id="d0d62-161">They're also straightforward to debug, especially when compared with ARM templates.</span></span>

<span data-ttu-id="d0d62-162">CLI do Azure scripts funcionam bem quando você precisa desmontar e reimplantar sua infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="d0d62-162">Azure CLI scripts work well when you need to tear down and redeploy your infrastructure.</span></span> <span data-ttu-id="d0d62-163">A atualização de um ambiente existente pode ser complicada.</span><span class="sxs-lookup"><span data-stu-id="d0d62-163">Updating an existing environment can be tricky.</span></span> <span data-ttu-id="d0d62-164">Muitos comandos da CLI não são idempotentes.</span><span class="sxs-lookup"><span data-stu-id="d0d62-164">Many CLI commands aren't idempotent.</span></span> <span data-ttu-id="d0d62-165">Isso significa que eles recriarão o recurso toda vez que forem executados, mesmo que o recurso já exista.</span><span class="sxs-lookup"><span data-stu-id="d0d62-165">That means they'll recreate the resource each time they're run, even if the resource already exists.</span></span> <span data-ttu-id="d0d62-166">Sempre é possível adicionar código que verifica a existência de cada recurso antes de criá-lo.</span><span class="sxs-lookup"><span data-stu-id="d0d62-166">It's always possible to add code that checks for the existence of each resource before creating it.</span></span> <span data-ttu-id="d0d62-167">Mas, ao fazer isso, seu script pode ficar inflado e difícil de gerenciar.</span><span class="sxs-lookup"><span data-stu-id="d0d62-167">But, doing so, your script can become bloated and difficult to manage.</span></span>

<span data-ttu-id="d0d62-168">Esses scripts também podem ser inseridos em pipelines do Azure DevOps como `Azure CLI tasks` .</span><span class="sxs-lookup"><span data-stu-id="d0d62-168">These scripts can also be embedded in Azure DevOps pipelines as `Azure CLI tasks`.</span></span> <span data-ttu-id="d0d62-169">A execução do pipeline invoca o script.</span><span class="sxs-lookup"><span data-stu-id="d0d62-169">Executing the pipeline invokes the script.</span></span>

<span data-ttu-id="d0d62-170">A Figura 10-17 mostra um trecho de código YAML que lista a versão do CLI do Azure e os detalhes da assinatura.</span><span class="sxs-lookup"><span data-stu-id="d0d62-170">Figure 10-17 shows a YAML snippet that lists the version of Azure CLI and the details of the subscription.</span></span> <span data-ttu-id="d0d62-171">Observe como CLI do Azure comandos são incluídos em um script embutido.</span><span class="sxs-lookup"><span data-stu-id="d0d62-171">Note how Azure CLI commands are included in an inline script.</span></span>

```yaml
- task: AzureCLI@2
  displayName: Azure CLI
  inputs:
    azureSubscription: <Name of the Azure Resource Manager service connection>
    scriptType: ps
    scriptLocation: inlineScript
    inlineScript: |
      az --version
      az account show
```

<span data-ttu-id="d0d62-172">**Figura 10-17** -CLI do Azure script</span><span class="sxs-lookup"><span data-stu-id="d0d62-172">**Figure 10-17** - Azure CLI script</span></span>

<span data-ttu-id="d0d62-173">No artigo, [o que é infraestrutura como código](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), autor Sam Guckenheimer descreve como "as equipes que implementam o IaC podem fornecer ambientes estáveis rapidamente e em escala.</span><span class="sxs-lookup"><span data-stu-id="d0d62-173">In the article, [What is Infrastructure as Code](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code), Author Sam Guckenheimer describes how, "Teams who implement IaC can deliver stable environments rapidly and at scale.</span></span> <span data-ttu-id="d0d62-174">As equipes evitam a configuração manual de ambientes e impõem a consistência, representando o estado desejado de seus ambientes por meio de código.</span><span class="sxs-lookup"><span data-stu-id="d0d62-174">Teams avoid manual configuration of environments and enforce consistency by representing the desired state of their environments via code.</span></span> <span data-ttu-id="d0d62-175">Implantações de infraestrutura com IaC são repetíveis e evitam problemas de tempo de execução causados por descompasso de configuração ou dependências ausentes.</span><span class="sxs-lookup"><span data-stu-id="d0d62-175">Infrastructure deployments with IaC are repeatable and prevent runtime issues caused by configuration drift or missing dependencies.</span></span> <span data-ttu-id="d0d62-176">As equipes do DevOps podem trabalhar junto com um conjunto unificado de práticas e ferramentas para fornecer aplicativos e sua infraestrutura de suporte de forma rápida, confiável e em escala. "</span><span class="sxs-lookup"><span data-stu-id="d0d62-176">DevOps teams can work together with a unified set of practices and tools to deliver applications and their supporting infrastructure rapidly, reliably, and at scale."</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d0d62-177">[Anterior](feature-flags.md) 
> [Avançar](application-bundles.md)</span><span class="sxs-lookup"><span data-stu-id="d0d62-177">[Previous](feature-flags.md)
[Next](application-bundles.md)</span></span>
