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
# <a name="infrastructure-as-code"></a>Infraestrutura como código

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Os aplicativos nativos de nuvem tendem a fazer uso de todos os tipos de componentes de PaaS (plataforma como serviço) fantásticos. Em uma plataforma de nuvem como o Azure, esses componentes podem incluir itens como armazenamento, barramento de serviço e o serviço Signalr. À medida que os aplicativos se tornam mais complicados, o número desses serviços em uso provavelmente aumentará. Assim como a entrega contínua quebrou o modelo tradicional de implantação em um ambiente manualmente, o ritmo rápido de alteração também quebrou o modelo de ter um grupo de ti centralizado gerenciar ambientes.

A criação de ambientes pode, e também ser automatizada. Há uma ampla variedade de ferramentas bem pensadas que podem facilitar o processo.

## <a name="azure-resource-manager-templates"></a>Modelos de Azure Resource Manager

Os modelos de Azure Resource Manager são uma linguagem baseada em JSON para definir vários recursos no Azure. O esquema básico é semelhante a Figura 11-10.

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

**Figura 11-10** -o esquema para um modelo do Resource Manager

Nesse modelo, é possível definir um contêiner de armazenamento dentro da seção de recursos da seguinte forma:
 
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

**Figura 11-11** -um exemplo de uma conta de armazenamento definida em um modelo do Resource Manager

Os modelos podem ser parametrizados para que um modelo possa ser reutilizado com configurações diferentes para definir ambientes de desenvolvimento, QA e produção. Isso ajuda a eliminar surpresas ao migrar para um ambiente superior configurado de forma diferente dos ambientes inferiores. Os recursos definidos em um modelo normalmente são todos criados dentro de um único grupo de recursos no Azure (é possível definir vários grupos de recursos em um único modelo do Resource Manager, mas incomum). Isso torna muito fácil excluir um ambiente apenas excluindo o grupo de recursos como um todo. A análise de custo também pode ser executada no nível do grupo de recursos, permitindo uma rápida contabilidade de quanto cada ambiente está custando.

Há muitos modelos de exemplo definidos no projeto de [modelos de início rápido do Azure](https://github.com/Azure/azure-quickstart-templates) no GitHub que darão um trecho ao iniciar em um novo modelo ou a adicionar a um existente.

Os modelos do Resource Manager podem ser executados de várias maneiras. Talvez a maneira mais simples seja simplesmente colá-las no portal do Azure. Para implantações experimentais, esse método pode ser muito rápido. Eles também podem ser executados como parte de um processo de compilação ou versão no Azure DevOps. Há tarefas que usarão conexões no Azure para executar os modelos. As alterações nos modelos do Resource Manager são aplicadas incrementalmente, o que significa que, para adicionar um novo recurso, é necessário apenas adicioná-lo ao modelo. As ferramentas tratarão de diferenciar o grupo de recursos atual com o grupo de recursos desejado definido no modelo. Os recursos serão criados ou alterados para que correspondam ao que está definido no modelo.  

## <a name="terraform"></a>Terraform

Uma desvantagem percebida dos modelos do Resource Manager é que eles são específicos para a nuvem do Azure. É incomum criar aplicativos que incluem recursos de mais de uma nuvem, mas nos casos em que a empresa depende de tempo de atividade espetacular, o custo de dar suporte a várias nuvens pode ser válido. Se houvesse uma linguagem de modelagem que pudesse ser usada em cada nuvem, ela também permitiria que as habilidades do desenvolvedor fossem muito mais portáveis.

Existem várias tecnologias que fazem exatamente isso! A oferta mais madura nesse espaço é conhecida como [Terraform](https://www.terraform.io/). O Terraform dá suporte a todos os principais players de nuvem, como o Azure, Google Cloud Platform, AWS e o, além de dar suporte a dezenas de jogadores secundários, como Heroku e DigitalOcean. Em vez de usar JSON como a linguagem de definição de modelo, ele usa o YAML ligeiramente mais conciso. 

Um arquivo Terraform de exemplo que faz o mesmo que o modelo do Resource Manager anterior (Figura 11-11) é mostrado na Figura 11-12:

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

**Figura 11-12** -um exemplo de um modelo do Resource Manager

O Terraform faz um trabalho melhor de fornecer mensagens de erro sensatas quando um recurso não pode ser implantado devido a um erro no modelo. Essa é uma área em que os modelos do Resource Manager têm alguns desafios contínuos. Também há uma tarefa de validação muito útil que pode ser usada na fase de compilação para detectar erros de modelo no início.

Assim como acontece com os modelos do Resource Manager, há ferramentas de linha de comando que podem ser usadas para implantar modelos Terraform. Também há tarefas criadas pela Comunidade no Azure Pipelines que podem validar e aplicar modelos Terraform.

Caso o modelo do Terraform ou do Resource Manager gere valores interessantes, como a cadeia de conexão para um banco de dados recém-criado, eles podem ser capturados no pipeline de compilação e usados em tarefas subsequentes.

>[!div class="step-by-step"]
>[Anterior](devops.md)
>[Próximo](application-bundles.md)
