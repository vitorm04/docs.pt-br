---
title: <section> Elemento
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c1675540df6844f98572c11cfb140bff23b31a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089025"
---
# <a name="section-element"></a><span data-ttu-id="c0e6e-102">elemento de > de seção \<</span><span class="sxs-lookup"><span data-stu-id="c0e6e-102">\<section> element</span></span>

<span data-ttu-id="c0e6e-103">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="c0e6e-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0e6e-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="c0e6e-105">&nbsp;&nbsp;[ **\<configsections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c0e6e-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="c0e6e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<seção >**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="c0e6e-107">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0e6e-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="c0e6e-108">&nbsp;&nbsp;[ **\<configsections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c0e6e-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="c0e6e-109">&nbsp;&nbsp;[ \**&nbsp;&nbsp;\<o >\** ](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="c0e6e-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\</span></span>
<span data-ttu-id="c0e6e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**seção**\<</span><span class="sxs-lookup"><span data-stu-id="c0e6e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c0e6e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0e6e-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="c0e6e-112">Atributos necessários</span><span class="sxs-lookup"><span data-stu-id="c0e6e-112">Required attributes</span></span>

|           | <span data-ttu-id="c0e6e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e6e-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c0e6e-114">**name**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-114">**name**</span></span>  | <span data-ttu-id="c0e6e-115">Especifica o nome da seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="c0e6e-116">**type**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-116">**type**</span></span>  | <span data-ttu-id="c0e6e-117">Especifica o nome da classe de manipulador da seção de configuração que lê a seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="c0e6e-118">O valor do tipo tem a sintaxe "totalmente qualificado-section-Handle-Class-Name, Simple-Assembly-Name".</span><span class="sxs-lookup"><span data-stu-id="c0e6e-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="c0e6e-119">O nome do assembly simples é o nome de arquivo raiz sem a extensão de arquivos *. dll* .</span><span class="sxs-lookup"><span data-stu-id="c0e6e-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="c0e6e-120">Atributos opcionais</span><span class="sxs-lookup"><span data-stu-id="c0e6e-120">Optional attributes</span></span>

<span data-ttu-id="c0e6e-121">Os atributos a seguir são aplicáveis somente para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="c0e6e-122">O sistema de configuração ignora esses atributos para outros tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="c0e6e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e6e-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="c0e6e-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-124">**allowDefinition**</span></span> | <span data-ttu-id="c0e6e-125">Especifica em qual arquivo de configuração a seção pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="c0e6e-126">Use um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c0e6e-126">Use one of the following values:</span></span><br><br><span data-ttu-id="c0e6e-127">**Parte**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-127">**Everywhere**</span></span><br><span data-ttu-id="c0e6e-128">Permite que a seção seja usada em qualquer arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="c0e6e-129">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-129">This is the default.</span></span><br><span data-ttu-id="c0e6e-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-130">**MachineOnly**</span></span><br><span data-ttu-id="c0e6e-131">Permite que a seção seja usada somente no arquivo de configuração da máquina (*Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="c0e6e-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="c0e6e-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-132">**MachineToApplication**</span></span><br><span data-ttu-id="c0e6e-133">Permite que a seção seja usada no arquivo de configuração do computador ou no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="c0e6e-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-134">**allowLocation**</span></span>   | <span data-ttu-id="c0e6e-135">Determina se a seção pode ser usada dentro do elemento **\<local >** .</span><span class="sxs-lookup"><span data-stu-id="c0e6e-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="c0e6e-136">Use um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c0e6e-136">Use one of the following values:</span></span><br><br><span data-ttu-id="c0e6e-137">**true**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-137">**true**</span></span><br><span data-ttu-id="c0e6e-138">Permite que a seção seja usada dentro do elemento **\<local >** .</span><span class="sxs-lookup"><span data-stu-id="c0e6e-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="c0e6e-139">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-139">This is the default.</span></span><br><span data-ttu-id="c0e6e-140">**false**</span><span class="sxs-lookup"><span data-stu-id="c0e6e-140">**false**</span></span><br><span data-ttu-id="c0e6e-141">Não permite que a seção seja usada dentro do elemento **\<local >** .</span><span class="sxs-lookup"><span data-stu-id="c0e6e-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="c0e6e-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0e6e-142">Parent elements</span></span>

|     | <span data-ttu-id="c0e6e-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0e6e-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c0e6e-144"> **\<configsections >** Elementos</span><span class="sxs-lookup"><span data-stu-id="c0e6e-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="c0e6e-145">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="c0e6e-146"> **\<> de seção** Elementos</span><span class="sxs-lookup"><span data-stu-id="c0e6e-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c0e6e-147">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="c0e6e-148">Um elemento de **> de seção\<** é um elemento filho de **\<configSections >** ou\<o > de **seção** , mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="c0e6e-149">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0e6e-149">Child elements</span></span>

<span data-ttu-id="c0e6e-150">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c0e6e-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="c0e6e-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0e6e-151">Remarks</span></span>

<span data-ttu-id="c0e6e-152">Declarar uma seção de configuração essencialmente define um novo elemento para o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="c0e6e-153">O novo elemento contém configurações que um manipulador de seção de configuração (ou seja, uma classe que implementa a interface de <xref:System.Configuration.IConfigurationSectionHandler>) lê.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="c0e6e-154">Os atributos e os elementos filho de uma seção que você define dependem do manipulador de seção que você usa para ler suas configurações.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="c0e6e-155">A declaração de um manipulador de seção de configuração no arquivo *Machine. config* permite que você use a seção de configuração em qualquer arquivo de configuração de aplicativo nesse computador, a menos que o atributo **AllowDefinition** especifique o contrário.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="c0e6e-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0e6e-156">Example</span></span>

<span data-ttu-id="c0e6e-157">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:</span><span class="sxs-lookup"><span data-stu-id="c0e6e-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="c0e6e-158">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c0e6e-158">Configuration file</span></span>

<span data-ttu-id="c0e6e-159">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0e6e-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0e6e-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0e6e-160">See also</span></span>

- [<span data-ttu-id="c0e6e-161">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c0e6e-161">Configuration file schema for the .NET Framework</span></span>](index.md)
