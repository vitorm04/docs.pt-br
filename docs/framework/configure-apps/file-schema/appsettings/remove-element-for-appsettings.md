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
ms.openlocfilehash: 121b1c4b124ba07ff3bd312fd3832d3da592f486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921289"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="c1af7-102">\<remover o elemento > \<para appSettings ></span><span class="sxs-lookup"><span data-stu-id="c1af7-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="c1af7-103">Remove as configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c1af7-103">Removes custom application settings.</span></span>

<span data-ttu-id="c1af7-104">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c1af7-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="c1af7-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="c1af7-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="c1af7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="c1af7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c1af7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1af7-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="c1af7-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c1af7-108">Attribute</span></span>

|         | <span data-ttu-id="c1af7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1af7-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="c1af7-110">**key**</span><span class="sxs-lookup"><span data-stu-id="c1af7-110">**key**</span></span> | <span data-ttu-id="c1af7-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c1af7-111">Required attribute.</span></span><br><br><span data-ttu-id="c1af7-112">Especifica o nome da chave a ser removida.</span><span class="sxs-lookup"><span data-stu-id="c1af7-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="c1af7-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="c1af7-113">Parent element</span></span>

|     | <span data-ttu-id="c1af7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1af7-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c1af7-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="c1af7-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="c1af7-116">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1af7-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c1af7-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1af7-117">Child elements</span></span>

<span data-ttu-id="c1af7-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c1af7-118">None</span></span>

## <a name="example"></a><span data-ttu-id="c1af7-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1af7-119">Example</span></span>

<span data-ttu-id="c1af7-120">O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="c1af7-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="c1af7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1af7-121">See also</span></span>

- [<span data-ttu-id="c1af7-122">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c1af7-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
