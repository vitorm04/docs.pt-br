---
title: Elemento <appSettings> para <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155525"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="896cf-102">Elemento \<appSettings> para \<configuration></span><span class="sxs-lookup"><span data-stu-id="896cf-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="896cf-103">Contém configurações de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="896cf-103">Contains custom application settings.</span></span> <span data-ttu-id="896cf-104">Esta é uma seção de configuração predefinida fornecida pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="896cf-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="896cf-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="896cf-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="896cf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="896cf-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="896cf-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="896cf-107">Attribute</span></span>

|           | <span data-ttu-id="896cf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="896cf-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="896cf-109">**Grupo**</span><span class="sxs-lookup"><span data-stu-id="896cf-109">**file**</span></span>  | <span data-ttu-id="896cf-110">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="896cf-110">Optional attribute.</span></span><br><br><span data-ttu-id="896cf-111">Especifica um caminho relativo para um arquivo externo que contém definições de configuração de aplicativo personalizadas.</span><span class="sxs-lookup"><span data-stu-id="896cf-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="896cf-112">O arquivo especificado contém o mesmo tipo de configurações que são especificadas nos **\<add>** elementos, e **\<remove>** **\<clear>** e usa o mesmo formato de par chave/valor que esses elementos.</span><span class="sxs-lookup"><span data-stu-id="896cf-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="896cf-113">O caminho especificado é relativo ao arquivo de configuração principal.</span><span class="sxs-lookup"><span data-stu-id="896cf-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="896cf-114">Para um aplicativo Windows Forms, essa é a pasta binária (como */bin/Debug*), não o local do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="896cf-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="896cf-115">Para aplicativos Web Forms, o caminho é relativo à raiz do aplicativo, em que o arquivo *Web. config* está localizado.</span><span class="sxs-lookup"><span data-stu-id="896cf-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="896cf-116">O tempo de execução ignora o atributo se o arquivo especificado não puder ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="896cf-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="896cf-117">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="896cf-117">Parent element</span></span>

|     | <span data-ttu-id="896cf-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="896cf-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="896cf-119">**\<configuration>** Elementos</span><span class="sxs-lookup"><span data-stu-id="896cf-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="896cf-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="896cf-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="896cf-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="896cf-121">Child elements</span></span>

|     | <span data-ttu-id="896cf-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="896cf-122">Description</span></span> |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | <span data-ttu-id="896cf-123">Adiciona uma configuração de aplicativo personalizada.</span><span class="sxs-lookup"><span data-stu-id="896cf-123">Adds a custom application setting.</span></span> |
| [**\<clear>**](clear-element-for-appsettings.md) | <span data-ttu-id="896cf-124">Limpa todas as configurações de aplicativo definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="896cf-124">Clears all previously defined application settings.</span></span> |
| [**\<remove>**](remove-element-for-appsettings.md) | <span data-ttu-id="896cf-125">Remove uma configuração de aplicativo definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="896cf-125">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="896cf-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="896cf-126">Remarks</span></span>

<span data-ttu-id="896cf-127">O **\<appSettings>** elemento armazena informações de configuração de aplicativo personalizadas, como cadeias de conexão de banco de dados, caminhos de arquivo, URLs de serviço Web XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="896cf-127">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="896cf-128">Os pares de chave/valor especificados no **\<appSettings>** elemento são acessados no código usando a <xref:System.Configuration.ConfigurationSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="896cf-128">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="896cf-129">Você pode usar o atributo **File** no **\<appSettings>** elemento dos arquivos *Web. config* e de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="896cf-129">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="896cf-130">Esse atributo especifica um arquivo de configuração que fornece configurações adicionais ou substitui as configurações especificadas no **\<appSettings>** elemento.</span><span class="sxs-lookup"><span data-stu-id="896cf-130">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="896cf-131">O atributo de **arquivo** pode ser usado em cenários de desenvolvimento de equipe de controle do código-fonte, como quando um usuário deseja substituir as configurações de projeto especificadas em um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="896cf-131">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="896cf-132">Os arquivos de configuração especificados pelo atributo de **arquivo** devem ter um nó raiz **\<appSettings>** em vez de **\<configuration>** .</span><span class="sxs-lookup"><span data-stu-id="896cf-132">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="896cf-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="896cf-133">Example</span></span>

<span data-ttu-id="896cf-134">O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:</span><span class="sxs-lookup"><span data-stu-id="896cf-134">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="896cf-135">O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="896cf-135">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="896cf-136">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="896cf-136">Configuration file</span></span>

<span data-ttu-id="896cf-137">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração do computador (*Machine. config*) e nos arquivos *Web. config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="896cf-137">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="896cf-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="896cf-138">See also</span></span>

- [<span data-ttu-id="896cf-139">Esquema do arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="896cf-139">Configuration file schema for the .NET Framework</span></span>](../index.md)
