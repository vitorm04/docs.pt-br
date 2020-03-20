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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155525"
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="c3f0e-102">\<appSettings> \<elemento para> de configuração</span><span class="sxs-lookup"><span data-stu-id="c3f0e-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="c3f0e-103">Contém configurações de aplicativos personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-103">Contains custom application settings.</span></span> <span data-ttu-id="c3f0e-104">Esta é uma seção de configuração predefinida fornecida pelo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="c3f0e-105">configuração &nbsp; &nbsp; [\*\* \<>\*\*](../configuration-element.md) \*\* \<aplicativosConfigurações>\*\*</span><span class="sxs-lookup"><span data-stu-id="c3f0e-105">[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c3f0e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3f0e-106">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="c3f0e-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="c3f0e-107">Attribute</span></span>

|           | <span data-ttu-id="c3f0e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3f0e-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c3f0e-109">**Arquivo**</span><span class="sxs-lookup"><span data-stu-id="c3f0e-109">**file**</span></span>  | <span data-ttu-id="c3f0e-110">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-110">Optional attribute.</span></span><br><br><span data-ttu-id="c3f0e-111">Especifica um caminho relativo a um arquivo externo contendo configurações personalizadas de configuração de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-111">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="c3f0e-112">O arquivo especificado contém o mesmo tipo de configurações \*\* \< \*\*especificadas no \*\* \<>de adicionar, **remover>e \*\* \<limpar elementos>** e usa o mesmo formato de par de tecla/valor que esses elementos.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-112">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="c3f0e-113">O caminho especificado é relativo ao arquivo de configuração principal.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-113">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="c3f0e-114">Para um aplicativo do Windows Forms, esta é a pasta binária (como */bin/depuração),* não a localização do arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-114">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="c3f0e-115">Para aplicativos web forms, o caminho é relativo à raiz do aplicativo, onde o arquivo *Web.config* está localizado.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-115">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="c3f0e-116">O tempo de execução ignora o atributo se o arquivo especificado não puder ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-116">The runtime ignores the attribute if the specified file can't be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c3f0e-117">Elemento pai</span><span class="sxs-lookup"><span data-stu-id="c3f0e-117">Parent element</span></span>

|     | <span data-ttu-id="c3f0e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3f0e-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c3f0e-119">>de configuração \*\* \<\*\* Elemento</span><span class="sxs-lookup"><span data-stu-id="c3f0e-119">**\<configuration>** Element</span></span>](../configuration-element.md) | <span data-ttu-id="c3f0e-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c3f0e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c3f0e-121">Child elements</span></span>

|     | <span data-ttu-id="c3f0e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3f0e-122">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c3f0e-123">**\<adicionar>**</span><span class="sxs-lookup"><span data-stu-id="c3f0e-123">**\<add>**</span></span>](add-element-for-appsettings.md) | <span data-ttu-id="c3f0e-124">Adiciona uma configuração de aplicativo personalizada.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-124">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="c3f0e-125">**\<claro>**</span><span class="sxs-lookup"><span data-stu-id="c3f0e-125">**\<clear>**</span></span>](clear-element-for-appsettings.md) | <span data-ttu-id="c3f0e-126">Limpa todas as configurações de aplicativo definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-126">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="c3f0e-127">**\<remover>**</span><span class="sxs-lookup"><span data-stu-id="c3f0e-127">**\<remove>**</span></span>](remove-element-for-appsettings.md) | <span data-ttu-id="c3f0e-128">Remove uma configuração de aplicativo definida anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-128">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c3f0e-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3f0e-129">Remarks</span></span>

<span data-ttu-id="c3f0e-130">O \*\* \<aplicativoConfigurações>\*\* elemento armazena informações personalizadas de configuração de aplicativos, como strings de conexão de banco de dados, caminhos de arquivo, URLs de serviço web XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-130">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="c3f0e-131">Os pares de chaves/valor especificados no \*\* \<elemento AppSettings\*\*><xref:System.Configuration.ConfigurationSettings> são acessados em código usando a classe.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-131">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="c3f0e-132">Você pode usar o atributo de **arquivo** no \*\* \<aplicativoConfigurações>\*\* elemento dos arquivos de configuração *web.config* e de configuração de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-132">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="c3f0e-133">Este atributo especifica um arquivo de configuração que fornece configurações adicionais ou substitui as configurações especificadas no elemento \*\* \<Deconfigurações>.\*\*</span><span class="sxs-lookup"><span data-stu-id="c3f0e-133">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="c3f0e-134">O atributo **de arquivo** pode ser usado em cenários de desenvolvimento da equipe de controle de origem, como quando um usuário deseja substituir as configurações de projeto especificadas em um arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-134">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="c3f0e-135">Os arquivos de configuração especificados pelo atributo **do arquivo** devem ter um nó raiz de \*\* \<configurações>\*\* em vez de \*\* \<>de configuração \*\*.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-135">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="c3f0e-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3f0e-136">Example</span></span>

<span data-ttu-id="c3f0e-137">O exemplo a seguir mostra um arquivo de configurações de aplicativo externo (*custom.config*) que define uma configuração de aplicativo personalizada:</span><span class="sxs-lookup"><span data-stu-id="c3f0e-137">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="c3f0e-138">O exemplo a seguir mostra um arquivo de configuração de aplicativo que consome a configuração no arquivo de configurações externas e define sua própria configuração de aplicativo:</span><span class="sxs-lookup"><span data-stu-id="c3f0e-138">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c3f0e-139">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c3f0e-139">Configuration file</span></span>

<span data-ttu-id="c3f0e-140">Esse elemento pode ser usado no arquivo de configuração do aplicativo, no arquivo de configuração da máquina *(Machine.config)* e nos arquivos *Web.config* que não estão no nível do diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3f0e-140">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3f0e-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3f0e-141">See also</span></span>

- [<span data-ttu-id="c3f0e-142">Esquema de arquivo de configuração para o Framework .NET</span><span class="sxs-lookup"><span data-stu-id="c3f0e-142">Configuration file schema for the .NET Framework</span></span>](../index.md)
