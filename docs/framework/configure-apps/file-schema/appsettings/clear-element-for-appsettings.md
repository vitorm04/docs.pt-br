---
title: '&lt;Desmarque&gt; elemento para &lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bc52e3149c213925ea64a8421ee65befeea4161e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184212"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="a0744-102">\<Limpar > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="a0744-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="a0744-103">Limpa as configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="a0744-103">Clears custom application settings.</span></span>

<span data-ttu-id="a0744-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a0744-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="a0744-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a0744-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="a0744-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Limpar >**</span><span class="sxs-lookup"><span data-stu-id="a0744-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a0744-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0744-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="a0744-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="a0744-108">Attributes</span></span>

<span data-ttu-id="a0744-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a0744-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="a0744-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="a0744-110">Parent element</span></span>

|     | <span data-ttu-id="a0744-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0744-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a0744-112">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="a0744-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="a0744-113">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço Web XML ou qualquer outra informação de configuração de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="a0744-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a0744-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a0744-114">Child elements</span></span>

<span data-ttu-id="a0744-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a0744-115">None</span></span>

## <a name="example"></a><span data-ttu-id="a0744-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0744-116">Example</span></span>

<span data-ttu-id="a0744-117">O exemplo a seguir mostra como limpar as configurações personalizadas:</span><span class="sxs-lookup"><span data-stu-id="a0744-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="a0744-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0744-118">See also</span></span>

- [<span data-ttu-id="a0744-119">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a0744-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
