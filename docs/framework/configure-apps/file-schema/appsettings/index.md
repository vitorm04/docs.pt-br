---
title: Esquema de configurações do aplicativo
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd836f9ebd4d22ad6542c1fadc204b1ea67d1c26
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300775"
---
# <a name="app-settings-schema"></a><span data-ttu-id="f7add-102">Esquema de configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="f7add-102">App Settings schema</span></span>

<span data-ttu-id="f7add-103">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7add-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="f7add-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f7add-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f7add-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f7add-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="f7add-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add>** ](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="f7add-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) </span></span>  
<span data-ttu-id="f7add-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear>** ](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span><span class="sxs-lookup"><span data-stu-id="f7add-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) </span></span>  
<span data-ttu-id="f7add-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<remove>** ](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span><span class="sxs-lookup"><span data-stu-id="f7add-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)</span></span>

| <span data-ttu-id="f7add-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7add-109">Element</span></span> | <span data-ttu-id="f7add-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7add-110">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="f7add-111"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="f7add-111">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="f7add-112">Contém as marcas **\<add>** , **\<clear>** e **\<remove>** para controlar as configurações de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7add-112">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f7add-113">Tem um atributo **file** opcional.</span><span class="sxs-lookup"><span data-stu-id="f7add-113">Has an optional **file** attribute.</span></span> |
| [<span data-ttu-id="f7add-114"> *\*\<add>** </span><span class="sxs-lookup"><span data-stu-id="f7add-114">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="f7add-115">Define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="f7add-115">Defines a setting.</span></span> <span data-ttu-id="f7add-116">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="f7add-116">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f7add-117">Requer os atributos **key** e **value**.</span><span class="sxs-lookup"><span data-stu-id="f7add-117">Requires **key** and **value** attributes.</span></span> |
| [<span data-ttu-id="f7add-118"> *\*\<clear>** </span><span class="sxs-lookup"><span data-stu-id="f7add-118">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="f7add-119">Limpa todas as configurações.</span><span class="sxs-lookup"><span data-stu-id="f7add-119">Clears all settings.</span></span> <span data-ttu-id="f7add-120">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="f7add-120">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f7add-121">Não tem atributos.</span><span class="sxs-lookup"><span data-stu-id="f7add-121">Has no attributes.</span></span> |
| [<span data-ttu-id="f7add-122"> *\*\<remove>** </span><span class="sxs-lookup"><span data-stu-id="f7add-122">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="f7add-123">Remove uma configuração.</span><span class="sxs-lookup"><span data-stu-id="f7add-123">Removes a setting.</span></span> <span data-ttu-id="f7add-124">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="f7add-124">Child of **\<appSettings>**.</span></span> <span data-ttu-id="f7add-125">Requer um atributo **key**.</span><span class="sxs-lookup"><span data-stu-id="f7add-125">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="f7add-126">Elemento \<appSettings></span><span class="sxs-lookup"><span data-stu-id="f7add-126">\<appSettings> element</span></span>

<span data-ttu-id="f7add-127">Esse elemento contém as marcas **\<add>** , **\<clear>** e **\<remove>** para controlar as configurações de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7add-127">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="f7add-128">Define um atributo opcional para **file**.</span><span class="sxs-lookup"><span data-stu-id="f7add-128">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="f7add-129">Elemento \<add></span><span class="sxs-lookup"><span data-stu-id="f7add-129">\<add> element</span></span>

<span data-ttu-id="f7add-130">Adiciona uma configuração de aplicativo personalizada como um par nome/valor para a coleção de configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7add-130">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="f7add-131">Define atributos de **key** e **value**.</span><span class="sxs-lookup"><span data-stu-id="f7add-131">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="f7add-132">Elemento \<clear></span><span class="sxs-lookup"><span data-stu-id="f7add-132">\<clear> element</span></span>

<span data-ttu-id="f7add-133">Remove todas as referências a configurações de aplicativo personalizadas herdadas e permite somente as referências que são adicionadas por elementos **\<add>** após o elemento **\<clear>** .</span><span class="sxs-lookup"><span data-stu-id="f7add-133">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="f7add-134">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="f7add-134">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="f7add-135">Elemento \<remove></span><span class="sxs-lookup"><span data-stu-id="f7add-135">\<remove> element</span></span>

<span data-ttu-id="f7add-136">Remove uma referência a uma configuração de aplicativo personalizada herdada da coleção de configurações de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7add-136">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="f7add-137">Define um atributo para **key**.</span><span class="sxs-lookup"><span data-stu-id="f7add-137">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="f7add-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7add-138">Example</span></span>

<span data-ttu-id="f7add-139">O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:</span><span class="sxs-lookup"><span data-stu-id="f7add-139">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="f7add-140">O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="f7add-140">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f7add-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7add-141">See also</span></span>

- [<span data-ttu-id="f7add-142">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="f7add-142">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="f7add-143">Arquitetura das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="f7add-143">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
