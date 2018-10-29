---
title: '&lt;Remova&gt; elemento para &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: e9b79a8319b320289f43adac5a82ef22fa5e32b0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199689"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="73f42-102">\<Remover > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="73f42-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="73f42-103">Remove as configurações de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="73f42-103">Removes custom application settings.</span></span>

<span data-ttu-id="73f42-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="73f42-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="73f42-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="73f42-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="73f42-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Remover >**</span><span class="sxs-lookup"><span data-stu-id="73f42-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="73f42-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73f42-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="73f42-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="73f42-108">Attribute</span></span>

|         | <span data-ttu-id="73f42-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f42-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="73f42-110">**key**</span><span class="sxs-lookup"><span data-stu-id="73f42-110">**key**</span></span> | <span data-ttu-id="73f42-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="73f42-111">Required attribute.</span></span><br><br><span data-ttu-id="73f42-112">Especifica o nome da chave a ser removido.</span><span class="sxs-lookup"><span data-stu-id="73f42-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="73f42-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="73f42-113">Parent element</span></span>

|     | <span data-ttu-id="73f42-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="73f42-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="73f42-115">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="73f42-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="73f42-116">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="73f42-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="73f42-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="73f42-117">Child elements</span></span>

<span data-ttu-id="73f42-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="73f42-118">None</span></span>

## <a name="example"></a><span data-ttu-id="73f42-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73f42-119">Example</span></span>

<span data-ttu-id="73f42-120">O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="73f42-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="73f42-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73f42-121">See also</span></span>

- [<span data-ttu-id="73f42-122">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="73f42-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
