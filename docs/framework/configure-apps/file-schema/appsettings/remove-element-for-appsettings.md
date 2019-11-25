---
title: Elemento <remove> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0fcdb75aa733a9d7634ec1c3b31dcbbb87e090e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088729"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="cf291-102">\<remover > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="cf291-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="cf291-103">Remove as configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="cf291-103">Removes custom application settings.</span></span>

<span data-ttu-id="cf291-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf291-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf291-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="cf291-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="cf291-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remover >**</span><span class="sxs-lookup"><span data-stu-id="cf291-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cf291-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf291-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="cf291-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cf291-108">Attribute</span></span>

|         | <span data-ttu-id="cf291-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf291-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="cf291-110">**key**</span><span class="sxs-lookup"><span data-stu-id="cf291-110">**key**</span></span> | <span data-ttu-id="cf291-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="cf291-111">Required attribute.</span></span><br><br><span data-ttu-id="cf291-112">Especifica o nome da chave a ser removida.</span><span class="sxs-lookup"><span data-stu-id="cf291-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="cf291-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="cf291-113">Parent element</span></span>

|     | <span data-ttu-id="cf291-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf291-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cf291-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="cf291-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="cf291-116">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cf291-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cf291-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cf291-117">Child elements</span></span>

<span data-ttu-id="cf291-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="cf291-118">None</span></span>

## <a name="example"></a><span data-ttu-id="cf291-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf291-119">Example</span></span>

<span data-ttu-id="cf291-120">O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="cf291-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="cf291-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf291-121">See also</span></span>

- [<span data-ttu-id="cf291-122">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cf291-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
