---
title: Elemento <remove> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215488"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="9d4c8-102">\<remover > elemento para \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="9d4c8-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="9d4c8-103">Remove as configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="9d4c8-103">Removes custom application settings.</span></span>

<span data-ttu-id="9d4c8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d4c8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9d4c8-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9d4c8-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="9d4c8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remover >**</span><span class="sxs-lookup"><span data-stu-id="9d4c8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9d4c8-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9d4c8-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="9d4c8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="9d4c8-108">Attribute</span></span>

|         | <span data-ttu-id="9d4c8-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="9d4c8-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="9d4c8-110">**chave**</span><span class="sxs-lookup"><span data-stu-id="9d4c8-110">**key**</span></span> | <span data-ttu-id="9d4c8-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9d4c8-111">Required attribute.</span></span><br><br><span data-ttu-id="9d4c8-112">Especifica o nome da chave a ser removida.</span><span class="sxs-lookup"><span data-stu-id="9d4c8-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="9d4c8-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="9d4c8-113">Parent element</span></span>

|     | <span data-ttu-id="9d4c8-114">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="9d4c8-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9d4c8-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="9d4c8-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="9d4c8-116">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d4c8-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9d4c8-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9d4c8-117">Child elements</span></span>

<span data-ttu-id="9d4c8-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9d4c8-118">None</span></span>

## <a name="example"></a><span data-ttu-id="9d4c8-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d4c8-119">Example</span></span>

<span data-ttu-id="9d4c8-120">O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="9d4c8-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9d4c8-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="9d4c8-121">See also</span></span>

- [<span data-ttu-id="9d4c8-122">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d4c8-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
