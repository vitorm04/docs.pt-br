---
title: Esquema de configurações do aplicativo
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215424"
---
# <a name="app-settings-schema"></a><span data-ttu-id="ec5ef-102">Esquema de configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ec5ef-102">App Settings schema</span></span>

<span data-ttu-id="ec5ef-103">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-103">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| <span data-ttu-id="ec5ef-104">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec5ef-104">Element</span></span> | <span data-ttu-id="ec5ef-105">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec5ef-105">Description</span></span> |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="ec5ef-106">Contém **\<add>** **\<clear>** marcas, e **\<remove>** para controlar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-106">Contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="ec5ef-107">Tem um atributo **file** opcional.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-107">Has an optional **file** attribute.</span></span> |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="ec5ef-108">Define uma configuração.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-108">Defines a setting.</span></span> <span data-ttu-id="ec5ef-109">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="ec5ef-109">Child of **\<appSettings>**.</span></span> <span data-ttu-id="ec5ef-110">Requer os atributos **key** e **value**.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-110">Requires **key** and **value** attributes.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="ec5ef-111">Limpa todas as configurações.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-111">Clears all settings.</span></span> <span data-ttu-id="ec5ef-112">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="ec5ef-112">Child of **\<appSettings>**.</span></span> <span data-ttu-id="ec5ef-113">Não tem atributos.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-113">Has no attributes.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="ec5ef-114">Remove uma configuração.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-114">Removes a setting.</span></span> <span data-ttu-id="ec5ef-115">Filho de **\<appSettings>** .</span><span class="sxs-lookup"><span data-stu-id="ec5ef-115">Child of **\<appSettings>**.</span></span> <span data-ttu-id="ec5ef-116">Requer um atributo **key**.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-116">Requires a **key** attribute.</span></span> |

## <a name="appsettings-element"></a><span data-ttu-id="ec5ef-117">Elemento \<appSettings></span><span class="sxs-lookup"><span data-stu-id="ec5ef-117">\<appSettings> element</span></span>

<span data-ttu-id="ec5ef-118">Este elemento contém **\<add>** **\<clear>** marcas, e **\<remove>** para controlar as configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-118">This element contains **\<add>**, **\<clear>**, and **\<remove>** tags to control application settings.</span></span> <span data-ttu-id="ec5ef-119">Define um atributo opcional para **file**.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-119">It defines an optional attribute for **file**.</span></span>

## <a name="add-element"></a><span data-ttu-id="ec5ef-120">Elemento \<add></span><span class="sxs-lookup"><span data-stu-id="ec5ef-120">\<add> element</span></span>

<span data-ttu-id="ec5ef-121">Adiciona uma configuração de aplicativo personalizada como um par nome/valor para a coleção de configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-121">Adds a custom application setting as a name/value pair to the application settings collection.</span></span> <span data-ttu-id="ec5ef-122">Define atributos de **key** e **value**.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-122">It defines attributes for **key** and **value**.</span></span>

## <a name="clear-element"></a><span data-ttu-id="ec5ef-123">Elemento \<clear></span><span class="sxs-lookup"><span data-stu-id="ec5ef-123">\<clear> element</span></span>

<span data-ttu-id="ec5ef-124">Remove todas as referências a configurações de aplicativo personalizadas herdadas e permite apenas as referências que são adicionadas por **\<add>** elementos que seguem o **\<clear>** elemento.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-124">Removes all references to inherited custom application settings and allows only the references that are added by **\<add>** elements following the **\<clear>** element.</span></span> <span data-ttu-id="ec5ef-125">Não define nenhum atributo.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-125">It defines no attributes.</span></span>

## <a name="remove-element"></a><span data-ttu-id="ec5ef-126">Elemento \<remove></span><span class="sxs-lookup"><span data-stu-id="ec5ef-126">\<remove> element</span></span>

<span data-ttu-id="ec5ef-127">Remove uma referência a uma configuração de aplicativo personalizada herdada da coleção de configurações de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-127">Removes a reference to an inherited custom application setting from the application settings collection.</span></span> <span data-ttu-id="ec5ef-128">Define um atributo para **key**.</span><span class="sxs-lookup"><span data-stu-id="ec5ef-128">It defines an attribute for **key**.</span></span>

## <a name="example"></a><span data-ttu-id="ec5ef-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ec5ef-129">Example</span></span>

<span data-ttu-id="ec5ef-130">O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:</span><span class="sxs-lookup"><span data-stu-id="ec5ef-130">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="ec5ef-131">O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ec5ef-131">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ec5ef-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec5ef-132">See also</span></span>

- [<span data-ttu-id="ec5ef-133">Visão geral das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ec5ef-133">Application Settings Overview</span></span>](../../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="ec5ef-134">Arquitetura das configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="ec5ef-134">Application Settings Architecture</span></span>](../../../winforms/advanced/application-settings-architecture.md)
