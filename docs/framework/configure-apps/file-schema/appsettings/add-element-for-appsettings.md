---
title: Elemento <add> para <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214806"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="dda5b-102">Elemento \<add> para \<appSettings></span><span class="sxs-lookup"><span data-stu-id="dda5b-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="dda5b-103">Adiciona uma configuração de aplicativo personalizada.</span><span class="sxs-lookup"><span data-stu-id="dda5b-103">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="dda5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dda5b-104">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="dda5b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="dda5b-105">Attributes</span></span>

|           | <span data-ttu-id="dda5b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="dda5b-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="dda5b-107">**chave**</span><span class="sxs-lookup"><span data-stu-id="dda5b-107">**key**</span></span>   | <span data-ttu-id="dda5b-108">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dda5b-108">Required attribute.</span></span><br><br><span data-ttu-id="dda5b-109">Especifica o nome da chave a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="dda5b-109">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="dda5b-110">**value**</span><span class="sxs-lookup"><span data-stu-id="dda5b-110">**value**</span></span> | <span data-ttu-id="dda5b-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dda5b-111">Required attribute.</span></span><br><br><span data-ttu-id="dda5b-112">Especifica o valor da chave a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="dda5b-112">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="dda5b-113">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="dda5b-113">Parent element</span></span>

|     | <span data-ttu-id="dda5b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dda5b-114">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="dda5b-115">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dda5b-115">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="dda5b-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dda5b-116">Child elements</span></span>

<span data-ttu-id="dda5b-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="dda5b-117">None</span></span>

## <a name="example"></a><span data-ttu-id="dda5b-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dda5b-118">Example</span></span>

<span data-ttu-id="dda5b-119">O exemplo a seguir mostra como adicionar uma definição de configuração personalizada para o nome do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="dda5b-119">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="dda5b-120">O exemplo a seguir usa o `<add>` elemento para definir duas configurações de compatibilidade em um aplicativo ASP.net:</span><span class="sxs-lookup"><span data-stu-id="dda5b-120">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="dda5b-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="dda5b-121">See also</span></span>

- [<span data-ttu-id="dda5b-122">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dda5b-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
