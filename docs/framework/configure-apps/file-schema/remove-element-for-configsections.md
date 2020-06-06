---
title: Elemento <remove> para <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154524"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="cfd30-102">Elemento \<remove> para \<configSections></span><span class="sxs-lookup"><span data-stu-id="cfd30-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="cfd30-103">Remove uma seção ou um grupo de seções predefinido.</span><span class="sxs-lookup"><span data-stu-id="cfd30-103">Removes a predefined section or section group.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="cfd30-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfd30-104">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="cfd30-105">Atributo</span><span class="sxs-lookup"><span data-stu-id="cfd30-105">Attribute</span></span>

|           | <span data-ttu-id="cfd30-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfd30-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cfd30-107">**name**</span><span class="sxs-lookup"><span data-stu-id="cfd30-107">**name**</span></span>  | <span data-ttu-id="cfd30-108">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cfd30-108">Required attribute.</span></span><br><br><span data-ttu-id="cfd30-109">Especifica o nome da seção ou do grupo de seções a ser removido.</span><span class="sxs-lookup"><span data-stu-id="cfd30-109">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="cfd30-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="cfd30-110">Parent element</span></span>

|     | <span data-ttu-id="cfd30-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="cfd30-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cfd30-112">**\<configSections>** Elementos</span><span class="sxs-lookup"><span data-stu-id="cfd30-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="cfd30-113">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="cfd30-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cfd30-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cfd30-114">Child elements</span></span>

<span data-ttu-id="cfd30-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cfd30-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="cfd30-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfd30-116">Remarks</span></span>

<span data-ttu-id="cfd30-117">Você pode usar o **\<remove>** elemento para remover seções e grupos de seções do seu aplicativo que foram definidos em um nível superior na hierarquia do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="cfd30-117">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="cfd30-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfd30-118">Example</span></span>

<span data-ttu-id="cfd30-119">O exemplo a seguir mostra como usar o **\<remove>** elemento em um arquivo de configuração de aplicativo para remover uma seção definida anteriormente no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="cfd30-119">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="cfd30-120">O código do arquivo de configuração do computador a seguir declara a seção **\<sampleSection>** :</span><span class="sxs-lookup"><span data-stu-id="cfd30-120">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1"
                 setting2="value two"
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="cfd30-121">O código do arquivo de configuração de aplicativo a seguir remove a **\<sampleSection>** seção.</span><span class="sxs-lookup"><span data-stu-id="cfd30-121">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="cfd30-122">Após a remoção, o aplicativo não pode recuperar as configurações no **\<sampleSection>** .</span><span class="sxs-lookup"><span data-stu-id="cfd30-122">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="cfd30-123">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="cfd30-123">Configuration file</span></span>

<span data-ttu-id="cfd30-124">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cfd30-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfd30-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfd30-125">See also</span></span>

- [<span data-ttu-id="cfd30-126">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cfd30-126">Configuration file schema for the .NET Framework</span></span>](index.md)
