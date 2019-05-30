---
title: Elemento <add> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: f8b426dc0e1e180afbfccce50d3b45774991a572
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301345"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="0e03a-102">\<Adicionar > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="0e03a-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="0e03a-103">Adiciona uma configuração de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="0e03a-103">Adds a custom application setting.</span></span>

<span data-ttu-id="0e03a-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0e03a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="0e03a-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="0e03a-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="0e03a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="0e03a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0e03a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e03a-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="0e03a-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="0e03a-108">Attributes</span></span>

|           | <span data-ttu-id="0e03a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e03a-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0e03a-110">**key**</span><span class="sxs-lookup"><span data-stu-id="0e03a-110">**key**</span></span>   | <span data-ttu-id="0e03a-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0e03a-111">Required attribute.</span></span><br><br><span data-ttu-id="0e03a-112">Especifica o nome da chave a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="0e03a-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="0e03a-113">**value**</span><span class="sxs-lookup"><span data-stu-id="0e03a-113">**value**</span></span> | <span data-ttu-id="0e03a-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0e03a-114">Required attribute.</span></span><br><br><span data-ttu-id="0e03a-115">Especifica o valor da chave a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="0e03a-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0e03a-116">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="0e03a-116">Parent element</span></span>

|     | <span data-ttu-id="0e03a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e03a-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0e03a-118"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="0e03a-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="0e03a-119">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e03a-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0e03a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0e03a-120">Child elements</span></span>

<span data-ttu-id="0e03a-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0e03a-121">None</span></span>

## <a name="example"></a><span data-ttu-id="0e03a-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e03a-122">Example</span></span>

<span data-ttu-id="0e03a-123">O exemplo a seguir mostra como adicionar uma definição de configuração personalizada para o nome do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0e03a-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="0e03a-124">O exemplo a seguir usa o `<add>` elemento para definir duas configurações de compatibilidade em um aplicativo ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="0e03a-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="0e03a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e03a-125">See also</span></span>

- [<span data-ttu-id="0e03a-126">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0e03a-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
