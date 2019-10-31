---
title: Esquema de configurações do aplicativo
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b931b76aa09b3f62fbd799990975268af4f7293
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119212"
---
# <a name="app-settings-schema"></a><span data-ttu-id="4e226-102">Esquema de configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e226-102">App Settings schema</span></span>

<span data-ttu-id="4e226-103">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e226-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="4e226-104">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4e226-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="4e226-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4e226-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="4e226-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="4e226-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="4e226-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear>** ](clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="4e226-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="4e226-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<remove>** ](remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="4e226-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="4e226-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="4e226-109">Element</span></span> | <span data-ttu-id="4e226-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e226-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="4e226-111"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="4e226-111">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="4e226-112">Contém as marcas **\<add>** , **\<clear>** e **\<remove>** para controlar as configurações de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e226-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="4e226-113">Tem um atributo **file** opcional.</span><span class="sxs-lookup"><span data-stu-id="4e226-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="4e226-114"> **\<add>** </span><span class="sxs-lookup"><span data-stu-id="4e226-114">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="4e226-115">Define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="4e226-115">Defines a setting.</span></span> <span data-ttu-id="4e226-116">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="4e226-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="4e226-117">Requer os atributos **key** e **value**.</span><span class="sxs-lookup"><span data-stu-id="4e226-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="4e226-118"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="4e226-118">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="4e226-119">Limpa todas as configurações.</span><span class="sxs-lookup"><span data-stu-id="4e226-119">Clears all settings.</span></span> <span data-ttu-id="4e226-120">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="4e226-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="4e226-121">Não tem atributos.</span><span class="sxs-lookup"><span data-stu-id="4e226-121">Has no attributes.</span></span> |
| [<span data-ttu-id="4e226-122"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="4e226-122">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="4e226-123">Remove uma configuração.</span><span class="sxs-lookup"><span data-stu-id="4e226-123">Removes a setting.</span></span> <span data-ttu-id="4e226-124">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="4e226-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="4e226-125">Requer um atributo **key**.</span><span class="sxs-lookup"><span data-stu-id="4e226-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="4e226-126">Elemento \<appSettings></span><span class="sxs-lookup"><span data-stu-id="4e226-126">\<appSettings> element</span></span>

<span data-ttu-id="4e226-127">Esse elemento contém as marcas **\<add>** , **\<clear>** e **\<remove>** para controlar as configurações de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e226-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="4e226-128">Define um atributo opcional para **file**.</span><span class="sxs-lookup"><span data-stu-id="4e226-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="4e226-129">Elemento \<add></span><span class="sxs-lookup"><span data-stu-id="4e226-129">\<add> element</span></span>

<span data-ttu-id="4e226-130">Adiciona uma configuração de aplicativo personalizada como um par nome/valor para a coleção de configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e226-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="4e226-131">Define atributos de **key** e **value**.</span><span class="sxs-lookup"><span data-stu-id="4e226-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="4e226-132">Elemento \<clear></span><span class="sxs-lookup"><span data-stu-id="4e226-132">\<clear> element</span></span>

<span data-ttu-id="4e226-133">Remove todas as referências a configurações de aplicativo personalizadas herdadas e permite somente as referências que são adicionadas por elementos **\<add>** após o elemento **\<clear>** .</span><span class="sxs-lookup"><span data-stu-id="4e226-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="4e226-134">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="4e226-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="4e226-135">Elemento \<remove></span><span class="sxs-lookup"><span data-stu-id="4e226-135">\<remove> element</span></span>

<span data-ttu-id="4e226-136">Remove uma referência a uma configuração de aplicativo personalizada herdada da coleção de configurações de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e226-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="4e226-137">Define um atributo para **key**.</span><span class="sxs-lookup"><span data-stu-id="4e226-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="4e226-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e226-138">Example</span></span>

<span data-ttu-id="4e226-139">O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:</span><span class="sxs-lookup"><span data-stu-id="4e226-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="4e226-140">O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="4e226-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4e226-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e226-141">See also</span></span>

- [<span data-ttu-id="4e226-142">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e226-142">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="4e226-143">Arquitetura das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="4e226-143">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
