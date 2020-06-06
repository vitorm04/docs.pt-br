---
title: <section> elemento
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153718"
---
# <a name="section-element"></a><span data-ttu-id="c0c87-102">Elemento \<section></span><span class="sxs-lookup"><span data-stu-id="c0c87-102">\<section> element</span></span>

<span data-ttu-id="c0c87-103">Contém uma declaração de seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c87-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="c0c87-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0c87-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="c0c87-105">Atributos obrigatórios</span><span class="sxs-lookup"><span data-stu-id="c0c87-105">Required attributes</span></span>

|           | <span data-ttu-id="c0c87-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0c87-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c0c87-107">**name**</span><span class="sxs-lookup"><span data-stu-id="c0c87-107">**name**</span></span>  | <span data-ttu-id="c0c87-108">Especifica o nome da seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c87-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="c0c87-109">**tipo**</span><span class="sxs-lookup"><span data-stu-id="c0c87-109">**type**</span></span>  | <span data-ttu-id="c0c87-110">Especifica o nome da classe de manipulador da seção de configuração que lê a seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c87-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="c0c87-111">O valor do tipo tem a sintaxe "totalmente qualificado-section-Handle-Class-Name, Simple-Assembly-Name".</span><span class="sxs-lookup"><span data-stu-id="c0c87-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="c0c87-112">O nome do assembly simples é o nome de arquivo raiz sem a extensão de arquivos *. dll* .</span><span class="sxs-lookup"><span data-stu-id="c0c87-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="c0c87-113">Atributos opcionais</span><span class="sxs-lookup"><span data-stu-id="c0c87-113">Optional attributes</span></span>

<span data-ttu-id="c0c87-114">Os atributos a seguir são aplicáveis somente para aplicativos ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c0c87-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="c0c87-115">O sistema de configuração ignora esses atributos para outros tipos de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c0c87-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="c0c87-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0c87-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="c0c87-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="c0c87-117">**allowDefinition**</span></span> | <span data-ttu-id="c0c87-118">Especifica em qual arquivo de configuração a seção pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="c0c87-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="c0c87-119">Use um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c0c87-119">Use one of the following values:</span></span><br><br><span data-ttu-id="c0c87-120">**Parte**</span><span class="sxs-lookup"><span data-stu-id="c0c87-120">**Everywhere**</span></span><br><span data-ttu-id="c0c87-121">Permite que a seção seja usada em qualquer arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c87-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="c0c87-122">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c0c87-122">This is the default.</span></span><br><span data-ttu-id="c0c87-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="c0c87-123">**MachineOnly**</span></span><br><span data-ttu-id="c0c87-124">Permite que a seção seja usada somente no arquivo de configuração da máquina (*Machine. config*).</span><span class="sxs-lookup"><span data-stu-id="c0c87-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="c0c87-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="c0c87-125">**MachineToApplication**</span></span><br><span data-ttu-id="c0c87-126">Permite que a seção seja usada no arquivo de configuração do computador ou no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0c87-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="c0c87-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="c0c87-127">**allowLocation**</span></span>   | <span data-ttu-id="c0c87-128">Determina se a seção pode ser usada dentro do **\<location>** elemento.</span><span class="sxs-lookup"><span data-stu-id="c0c87-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="c0c87-129">Use um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="c0c87-129">Use one of the following values:</span></span><br><br><span data-ttu-id="c0c87-130">**true**</span><span class="sxs-lookup"><span data-stu-id="c0c87-130">**true**</span></span><br><span data-ttu-id="c0c87-131">Permite que a seção seja usada dentro do **\<location>** elemento.</span><span class="sxs-lookup"><span data-stu-id="c0c87-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="c0c87-132">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c0c87-132">This is the default.</span></span><br><span data-ttu-id="c0c87-133">**false**</span><span class="sxs-lookup"><span data-stu-id="c0c87-133">**false**</span></span><br><span data-ttu-id="c0c87-134">Não permite que a seção seja usada dentro do **\<location>** elemento.</span><span class="sxs-lookup"><span data-stu-id="c0c87-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="c0c87-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c0c87-135">Parent elements</span></span>

|     | <span data-ttu-id="c0c87-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="c0c87-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c0c87-137">**\<configSections>** Elementos</span><span class="sxs-lookup"><span data-stu-id="c0c87-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="c0c87-138">Contém as declarações de namespace e seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c87-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="c0c87-139">**\<sectionGroup>** Elementos</span><span class="sxs-lookup"><span data-stu-id="c0c87-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="c0c87-140">Define um namespace para seções de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c87-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="c0c87-141">Um **\<section>** elemento é um elemento filho de **\<configSections>** ou **\<sectionGroup>** , mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="c0c87-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="c0c87-142">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c0c87-142">Child elements</span></span>

<span data-ttu-id="c0c87-143">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c0c87-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="c0c87-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="c0c87-144">Remarks</span></span>

<span data-ttu-id="c0c87-145">Declarar uma seção de configuração essencialmente define um novo elemento para o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c87-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="c0c87-146">O novo elemento contém configurações que um manipulador de seção de configuração (ou seja, uma classe que implementa a <xref:System.Configuration.IConfigurationSectionHandler> interface) lê.</span><span class="sxs-lookup"><span data-stu-id="c0c87-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="c0c87-147">Os atributos e os elementos filho de uma seção que você define dependem do manipulador de seção que você usa para ler suas configurações.</span><span class="sxs-lookup"><span data-stu-id="c0c87-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="c0c87-148">A declaração de um manipulador de seção de configuração no arquivo *Machine. config* permite que você use a seção de configuração em qualquer arquivo de configuração de aplicativo nesse computador, a menos que o atributo **AllowDefinition** especifique o contrário.</span><span class="sxs-lookup"><span data-stu-id="c0c87-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="c0c87-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0c87-149">Example</span></span>

<span data-ttu-id="c0c87-150">O exemplo a seguir mostra como definir uma seção de configuração e definir as configurações para essa seção:</span><span class="sxs-lookup"><span data-stu-id="c0c87-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="c0c87-151">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c0c87-151">Configuration file</span></span>

<span data-ttu-id="c0c87-152">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c0c87-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0c87-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0c87-153">See also</span></span>

- [<span data-ttu-id="c0c87-154">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c0c87-154">Configuration file schema for the .NET Framework</span></span>](index.md)
