---
title: '<section> Elemento '
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 64556054df2689ff758f52c7e98556997a3e9d3d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301180"
---
# <a name="section-element"></a><span data-ttu-id="d0e71-102">\<seção > elemento</span><span class="sxs-lookup"><span data-stu-id="d0e71-102">\<section> element</span></span>

<span data-ttu-id="d0e71-103">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0e71-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="d0e71-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d0e71-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d0e71-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d0e71-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="d0e71-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<section>**</span><span class="sxs-lookup"><span data-stu-id="d0e71-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="d0e71-107">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d0e71-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d0e71-108">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d0e71-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="d0e71-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup>** ](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="d0e71-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="d0e71-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<section>**</span><span class="sxs-lookup"><span data-stu-id="d0e71-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d0e71-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0e71-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="d0e71-112">Atributos obrigatórios</span><span class="sxs-lookup"><span data-stu-id="d0e71-112">Required attributes</span></span>

|           | <span data-ttu-id="d0e71-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0e71-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d0e71-114">**name**</span><span class="sxs-lookup"><span data-stu-id="d0e71-114">**name**</span></span>  | <span data-ttu-id="d0e71-115">Especifica o nome da seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0e71-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="d0e71-116">**type**</span><span class="sxs-lookup"><span data-stu-id="d0e71-116">**type**</span></span>  | <span data-ttu-id="d0e71-117">Especifica o nome da classe de manipulador de seção de configuração que lê a seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0e71-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="d0e71-118">O valor do tipo tem a sintaxe "fully-qualified-section-handler-class-name-simple-assembly-name".</span><span class="sxs-lookup"><span data-stu-id="d0e71-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="d0e71-119">O nome de assembly simples é o nome do arquivo raiz sem a *. dll* extensão de arquivo.</span><span class="sxs-lookup"><span data-stu-id="d0e71-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="d0e71-120">Atributos opcionais</span><span class="sxs-lookup"><span data-stu-id="d0e71-120">Optional attributes</span></span>

<span data-ttu-id="d0e71-121">Os atributos a seguir são aplicáveis apenas para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d0e71-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="d0e71-122">O sistema de configuração ignorará esses atributos para outros tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d0e71-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="d0e71-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0e71-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="d0e71-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="d0e71-124">**allowDefinition**</span></span> | <span data-ttu-id="d0e71-125">Especifica qual arquivo de configuração, a seção pode ser usada em.</span><span class="sxs-lookup"><span data-stu-id="d0e71-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="d0e71-126">Use um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d0e71-126">Use one of the following values:</span></span><br><br><span data-ttu-id="d0e71-127">**Everywhere**</span><span class="sxs-lookup"><span data-stu-id="d0e71-127">**Everywhere**</span></span><br><span data-ttu-id="d0e71-128">Permite que a seção a ser usado em qualquer arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0e71-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="d0e71-129">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d0e71-129">This is the default.</span></span><br><span data-ttu-id="d0e71-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="d0e71-130">**MachineOnly**</span></span><br><span data-ttu-id="d0e71-131">Permite que a seção a ser usado apenas no arquivo de configuração do computador (*Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="d0e71-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="d0e71-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="d0e71-132">**MachineToApplication**</span></span><br><span data-ttu-id="d0e71-133">Permite que a seção a ser usado no arquivo de configuração do computador ou o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0e71-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="d0e71-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="d0e71-134">**allowLocation**</span></span>   | <span data-ttu-id="d0e71-135">Determina se a seção pode ser usada dentro de  **\<local >** elemento.</span><span class="sxs-lookup"><span data-stu-id="d0e71-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="d0e71-136">Use um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d0e71-136">Use one of the following values:</span></span><br><br><span data-ttu-id="d0e71-137">**true**</span><span class="sxs-lookup"><span data-stu-id="d0e71-137">**true**</span></span><br><span data-ttu-id="d0e71-138">Permite que a seção a ser usado dentro de  **\<local >** elemento.</span><span class="sxs-lookup"><span data-stu-id="d0e71-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="d0e71-139">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d0e71-139">This is the default.</span></span><br><span data-ttu-id="d0e71-140">**false**</span><span class="sxs-lookup"><span data-stu-id="d0e71-140">**false**</span></span><br><span data-ttu-id="d0e71-141">Não permite a seção a ser usado dentro de  **\<local >** elemento.</span><span class="sxs-lookup"><span data-stu-id="d0e71-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="d0e71-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0e71-142">Parent elements</span></span>

|     | <span data-ttu-id="d0e71-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0e71-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d0e71-144"> *\*\<configSections>** Element</span><span class="sxs-lookup"><span data-stu-id="d0e71-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="d0e71-145">Contém as declarações de namespace e a seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0e71-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="d0e71-146"> *\*\<sectionGroup >** elemento</span><span class="sxs-lookup"><span data-stu-id="d0e71-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="d0e71-147">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0e71-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="d0e71-148">Um  **\<seção >** é um elemento filho de um  **\<configSections >** ou  **\<sectionGroup >** , mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="d0e71-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="d0e71-149">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0e71-149">Child elements</span></span>

<span data-ttu-id="d0e71-150">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d0e71-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d0e71-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0e71-151">Remarks</span></span>

<span data-ttu-id="d0e71-152">Declarar uma seção de configuração essencialmente define um novo elemento para o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d0e71-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="d0e71-153">O novo elemento contém definições de configuração de uma manipulador de seção (ou seja, uma classe que implementa o <xref:System.Configuration.IConfigurationSectionHandler> interface) lê.</span><span class="sxs-lookup"><span data-stu-id="d0e71-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="d0e71-154">Os atributos e elementos filho de uma seção que você define dependem do manipulador de seção, que você usa para ler suas configurações.</span><span class="sxs-lookup"><span data-stu-id="d0e71-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="d0e71-155">Declarando um manipulador de seção de configuração na *Machine. config* arquivo permite que você use a seção de configuração em qualquer arquivo de configuração de aplicativo nesse computador, a menos que o **allowDefinition**atributo especifique o contrário.</span><span class="sxs-lookup"><span data-stu-id="d0e71-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="d0e71-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0e71-156">Example</span></span>

<span data-ttu-id="d0e71-157">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações dessa seção:</span><span class="sxs-lookup"><span data-stu-id="d0e71-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d0e71-158">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="d0e71-158">Configuration file</span></span>

<span data-ttu-id="d0e71-159">Esse elemento pode ser usado no arquivo de configuração do aplicativo, arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0e71-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0e71-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0e71-160">See also</span></span>

- [<span data-ttu-id="d0e71-161">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0e71-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
