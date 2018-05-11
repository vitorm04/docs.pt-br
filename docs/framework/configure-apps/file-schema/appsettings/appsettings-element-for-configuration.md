---
title: '&lt;appSettings&gt; elemento para &lt;configuração&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: d17400536b911ce0be4d2bf105b0b4d99d0916df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="db043-102">\<appSettings > elemento \<Configuração ></span><span class="sxs-lookup"><span data-stu-id="db043-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="db043-103">Contém configurações de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="db043-103">Contains custom application settings.</span></span> <span data-ttu-id="db043-104">Essa é uma seção de configuração predefinidos fornecida pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db043-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="db043-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="db043-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="db043-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="db043-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="db043-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db043-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="db043-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="db043-108">Attribute</span></span>

|           | <span data-ttu-id="db043-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="db043-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="db043-110">**file**</span><span class="sxs-lookup"><span data-stu-id="db043-110">**file**</span></span>  | <span data-ttu-id="db043-111">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="db043-111">Optional attribute.</span></span><br><br><span data-ttu-id="db043-112">Especifica um caminho relativo para um arquivo externo que contém as definições de configuração de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="db043-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="db043-113">O arquivo especificado contém o mesmo tipo de configurações que são especificados no  **\<Adicionar >**,  **\<remover >**, e  **\<limpar >** elementos e usa o mesmo par chave/valor de formato como esses elementos.</span><span class="sxs-lookup"><span data-stu-id="db043-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="db043-114">O caminho especificado é relativo ao arquivo de configuração principais.</span><span class="sxs-lookup"><span data-stu-id="db043-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="db043-115">Para um aplicativo de formulários do Windows, essa é a pasta de binária (como */bin/debug*), não o local do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db043-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="db043-116">Para aplicativos de formulários da Web, o caminho é relativo a raiz do aplicativo, onde o *Web. config* arquivo está localizado.</span><span class="sxs-lookup"><span data-stu-id="db043-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="db043-117">Observe que o tempo de execução ignora o atributo se o arquivo especificado não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="db043-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="db043-118">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="db043-118">Parent element</span></span>

|     | <span data-ttu-id="db043-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="db043-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="db043-120">**\<Configuração >** elemento</span><span class="sxs-lookup"><span data-stu-id="db043-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="db043-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db043-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="db043-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="db043-122">Child elements</span></span>

|     | <span data-ttu-id="db043-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="db043-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="db043-124">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="db043-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="db043-125">Adiciona uma configuração de aplicativo personalizado.</span><span class="sxs-lookup"><span data-stu-id="db043-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="db043-126">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="db043-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="db043-127">Limpa todas as configurações de aplicativo definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="db043-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="db043-128">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="db043-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="db043-129">Remove uma configuração de aplicativo definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="db043-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="db043-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="db043-130">Remarks</span></span>

<span data-ttu-id="db043-131">O  **\<appSettings >** elemento armazena informações de configuração de aplicativo personalizado, como cadeias de conexão de banco de dados, os caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db043-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="db043-132">Os pares chave/valor especificados no  **\<appSettings >** elemento são acessadas em código usando o <xref:System.Configuration.ConfigurationSettings> classe.</span><span class="sxs-lookup"><span data-stu-id="db043-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="db043-133">Você pode usar o **arquivo** atributo no  **\<appSettings >** elemento o *Web. config* e arquivos de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db043-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="db043-134">Esse atributo especifica um arquivo de configuração que fornece configurações adicionais ou substitui as configurações especificadas no  **\<appSettings >** elemento.</span><span class="sxs-lookup"><span data-stu-id="db043-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="db043-135">O **arquivo** atributo pode ser usado na origem controle team cenários de desenvolvimento, como quando um usuário deseja substituir as configurações de projeto especificadas em um arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db043-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="db043-136">Arquivos de configuração especificados pelo **arquivo** atributo deve ter um nó de raiz de  **\<appSettings >** em vez de  **\<Configuração >**.</span><span class="sxs-lookup"><span data-stu-id="db043-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="db043-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="db043-137">Example</span></span>

<span data-ttu-id="db043-138">O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:</span><span class="sxs-lookup"><span data-stu-id="db043-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="db043-139">O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="db043-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="db043-140">arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="db043-140">Configuration file</span></span>

<span data-ttu-id="db043-141">Esse elemento pode ser usado no arquivo de configuração do aplicativo, o arquivo de configuração de máquina (*Machine. config*), e *Web. config* arquivos que não estão no nível de diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db043-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="db043-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db043-142">See also</span></span>

[<span data-ttu-id="db043-143">Esquema de arquivo de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db043-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
