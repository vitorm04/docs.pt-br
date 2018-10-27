---
title: '&lt;Adicione&gt; elemento para &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: e74f0956dd5acebccee87fd6ad8c09b299badffd
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50036379"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="06728-102">\<Adicionar > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="06728-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="06728-103">Adiciona uma configuração de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="06728-103">Adds a custom application setting.</span></span>

<span data-ttu-id="06728-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="06728-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="06728-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="06728-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="06728-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="06728-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="06728-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06728-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="06728-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="06728-108">Attributes</span></span>

|           | <span data-ttu-id="06728-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="06728-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="06728-110">**key**</span><span class="sxs-lookup"><span data-stu-id="06728-110">**key**</span></span>   | <span data-ttu-id="06728-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="06728-111">Required attribute.</span></span><br><br><span data-ttu-id="06728-112">Especifica o nome da chave a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="06728-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="06728-113">**value**</span><span class="sxs-lookup"><span data-stu-id="06728-113">**value**</span></span> | <span data-ttu-id="06728-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="06728-114">Required attribute.</span></span><br><br><span data-ttu-id="06728-115">Especifica o valor da chave a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="06728-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="06728-116">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="06728-116">Parent element</span></span>

|     | <span data-ttu-id="06728-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="06728-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="06728-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="06728-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="06728-119">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="06728-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="06728-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="06728-120">Child elements</span></span>

<span data-ttu-id="06728-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="06728-121">None</span></span>

## <a name="example"></a><span data-ttu-id="06728-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06728-122">Example</span></span>

<span data-ttu-id="06728-123">O exemplo a seguir mostra como adicionar uma definição de configuração personalizada para o nome do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="06728-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="06728-124">O exemplo a seguir usa o `<add>` elemento para definir duas configurações de compatibilidade em um aplicativo ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="06728-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="06728-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06728-125">See also</span></span>

- [<span data-ttu-id="06728-126">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06728-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
