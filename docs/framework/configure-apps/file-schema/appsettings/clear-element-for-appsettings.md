---
title: Elemento <clear> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d4d96143dbd1db440de2247a7dc2f0c66f20403
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301293"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="659b3-102">\<Limpar > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="659b3-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="659b3-103">Limpa as configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="659b3-103">Clears custom application settings.</span></span>

<span data-ttu-id="659b3-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="659b3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="659b3-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="659b3-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="659b3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="659b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="659b3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="659b3-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="659b3-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="659b3-108">Attributes</span></span>

<span data-ttu-id="659b3-109">Nenhum</span><span class="sxs-lookup"><span data-stu-id="659b3-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="659b3-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="659b3-110">Parent element</span></span>

|     | <span data-ttu-id="659b3-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="659b3-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="659b3-112"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="659b3-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="659b3-113">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço Web XML ou qualquer outra informação de configuração de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="659b3-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="659b3-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="659b3-114">Child elements</span></span>

<span data-ttu-id="659b3-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="659b3-115">None</span></span>

## <a name="example"></a><span data-ttu-id="659b3-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="659b3-116">Example</span></span>

<span data-ttu-id="659b3-117">O exemplo a seguir mostra como limpar as configurações personalizadas:</span><span class="sxs-lookup"><span data-stu-id="659b3-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="659b3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="659b3-118">See also</span></span>

- [<span data-ttu-id="659b3-119">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="659b3-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
