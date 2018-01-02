---
title: '&lt;Adicionar&gt; elemento para &lt;appSettings&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d080a7c63ddda0577e66d2e7ddd433c7fd5fdbd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="a79b8-102">\<Adicionar > elemento \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="a79b8-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="a79b8-103">Adiciona uma configuração de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="a79b8-103">Adds a custom application setting.</span></span>

<span data-ttu-id="a79b8-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a79b8-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a79b8-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a79b8-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="a79b8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="a79b8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a79b8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a79b8-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="a79b8-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a79b8-108">Attributes</span></span>

|           | <span data-ttu-id="a79b8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a79b8-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a79b8-110">**key**</span><span class="sxs-lookup"><span data-stu-id="a79b8-110">**key**</span></span>   | <span data-ttu-id="a79b8-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a79b8-111">Required attribute.</span></span><br><br><span data-ttu-id="a79b8-112">Especifica o nome da chave para adicionar.</span><span class="sxs-lookup"><span data-stu-id="a79b8-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="a79b8-113">**value**</span><span class="sxs-lookup"><span data-stu-id="a79b8-113">**value**</span></span> | <span data-ttu-id="a79b8-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a79b8-114">Required attribute.</span></span><br><br><span data-ttu-id="a79b8-115">Especifica o valor da chave para adicionar.</span><span class="sxs-lookup"><span data-stu-id="a79b8-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a79b8-116">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a79b8-116">Parent element</span></span>

|     | <span data-ttu-id="a79b8-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a79b8-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a79b8-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="a79b8-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="a79b8-119">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a79b8-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a79b8-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a79b8-120">Child elements</span></span>

<span data-ttu-id="a79b8-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a79b8-121">None</span></span>

## <a name="example"></a><span data-ttu-id="a79b8-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a79b8-122">Example</span></span>

<span data-ttu-id="a79b8-123">O exemplo a seguir mostra como adicionar uma configuração personalizada para o nome do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="a79b8-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="a79b8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a79b8-124">See also</span></span>

[<span data-ttu-id="a79b8-125">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a79b8-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
