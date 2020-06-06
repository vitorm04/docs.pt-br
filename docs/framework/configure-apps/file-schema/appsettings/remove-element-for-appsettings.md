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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215488"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="022f8-102">Elemento \<remove> para \<appSettings></span><span class="sxs-lookup"><span data-stu-id="022f8-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="022f8-103">Remove as configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="022f8-103">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="022f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="022f8-104">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="022f8-105">Atributo</span><span class="sxs-lookup"><span data-stu-id="022f8-105">Attribute</span></span>

|         | <span data-ttu-id="022f8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="022f8-106">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="022f8-107">**chave**</span><span class="sxs-lookup"><span data-stu-id="022f8-107">**key**</span></span> | <span data-ttu-id="022f8-108">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="022f8-108">Required attribute.</span></span><br><br><span data-ttu-id="022f8-109">Especifica o nome da chave a ser removida.</span><span class="sxs-lookup"><span data-stu-id="022f8-109">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="022f8-110">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="022f8-110">Parent element</span></span>

|     | <span data-ttu-id="022f8-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="022f8-111">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="022f8-112">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="022f8-112">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="022f8-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="022f8-113">Child elements</span></span>

<span data-ttu-id="022f8-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="022f8-114">None</span></span>

## <a name="example"></a><span data-ttu-id="022f8-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="022f8-115">Example</span></span>

<span data-ttu-id="022f8-116">O exemplo a seguir mostra como remover uma configuração personalizada para `ApplicationName` :</span><span class="sxs-lookup"><span data-stu-id="022f8-116">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="022f8-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="022f8-117">See also</span></span>

- [<span data-ttu-id="022f8-118">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="022f8-118">Configuration file schema for the .NET Framework</span></span>](../index.md)
