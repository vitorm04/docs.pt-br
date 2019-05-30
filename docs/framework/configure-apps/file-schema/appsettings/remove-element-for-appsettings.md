---
title: Elemento <remove> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 62913face910ae9500aa5e6f2f443db67ffd4240
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301272"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="e9015-102">\<Remover > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="e9015-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="e9015-103">Remove as configurações de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="e9015-103">Removes custom application settings.</span></span>

<span data-ttu-id="e9015-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e9015-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="e9015-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e9015-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="e9015-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="e9015-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e9015-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9015-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="e9015-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e9015-108">Attribute</span></span>

|         | <span data-ttu-id="e9015-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9015-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="e9015-110">**key**</span><span class="sxs-lookup"><span data-stu-id="e9015-110">**key**</span></span> | <span data-ttu-id="e9015-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e9015-111">Required attribute.</span></span><br><br><span data-ttu-id="e9015-112">Especifica o nome da chave a ser removido.</span><span class="sxs-lookup"><span data-stu-id="e9015-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="e9015-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="e9015-113">Parent element</span></span>

|     | <span data-ttu-id="e9015-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9015-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e9015-115"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="e9015-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="e9015-116">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e9015-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e9015-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e9015-117">Child elements</span></span>

<span data-ttu-id="e9015-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e9015-118">None</span></span>

## <a name="example"></a><span data-ttu-id="e9015-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9015-119">Example</span></span>

<span data-ttu-id="e9015-120">O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="e9015-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="e9015-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9015-121">See also</span></span>

- [<span data-ttu-id="e9015-122">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9015-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
