---
title: Esquema de arquivos de configuração para o .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4543802c3918a4761daa5a4fbbab366695823f73
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028233"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="7b072-102">Esquema de arquivos de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b072-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="7b072-103">Arquivos de configuração são arquivos XML padrão que você pode usar para alterar as configurações e definir diretivas para seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7b072-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="7b072-104">O esquema de configuração do .NET Framework consiste em elementos que você pode usar em arquivos de configuração para controlar o comportamento de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7b072-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="7b072-105">O sumário desta seção reflete a hierarquia de esquema para inicialização, tempo de execução, rede e outros tipos de configuração.</span><span class="sxs-lookup"><span data-stu-id="7b072-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="7b072-106">Para obter informações sobre os tipos, o formato e o local dos arquivos de configuração, consulte o artigo [Configuring Apps](~/docs/framework/configure-apps/index.md) (Configurando aplicativos).</span><span class="sxs-lookup"><span data-stu-id="7b072-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](~/docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="7b072-107">Familiarize-se com XML para editar os arquivos de configuração diretamente.</span><span class="sxs-lookup"><span data-stu-id="7b072-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b072-108">Os atributos e as marcas XML em arquivos de configuração diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="7b072-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7b072-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7b072-109">In this section</span></span>

<span data-ttu-id="7b072-110">[Elemento **\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) Descreve o elemento `<configuration>`, que é o elemento de nível superior de todos os arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="7b072-110">[**\<configuration>** Element](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="7b072-111">[Elemento **\<assemblyBinding>**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Especifica a política de associação de assembly no nível da configuração.</span><span class="sxs-lookup"><span data-stu-id="7b072-111">[**\<assemblyBinding>** Element](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="7b072-112">[Elemento **\<linkedConfiguration>**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="7b072-112">[**\<linkedConfiguration>** Element](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="7b072-113">[Esquema de configurações de inicialização](~/docs/framework/configure-apps/file-schema/startup/index.md) Descreve os elementos que especificam qual versão do Common Language Runtime deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="7b072-113">[Startup Settings Schema](~/docs/framework/configure-apps/file-schema/startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="7b072-114">[Esquema de configurações de tempo de execução](~/docs/framework/configure-apps/file-schema/runtime/index.md) Descreve os elementos que configuram o comportamento de associação e do tempo de execução do assembly.</span><span class="sxs-lookup"><span data-stu-id="7b072-114">[Runtime Settings Schema](~/docs/framework/configure-apps/file-schema/runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="7b072-115">[Esquema de configurações de rede](~/docs/framework/configure-apps/file-schema/network/index.md) Descreve os elementos que especificam como o .NET Framework se conecta à Internet.</span><span class="sxs-lookup"><span data-stu-id="7b072-115">[Network Settings Schema](~/docs/framework/configure-apps/file-schema/network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="7b072-116">[Esquema de configurações de criptografia](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Descreve os elementos que mapeiam nomes de algoritmo amigáveis para classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="7b072-116">[Cryptography Settings Schema](~/docs/framework/configure-apps/file-schema/cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="7b072-117">[Esquema de seções de configuração](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Descreve os elementos usados para criar e usar as seções de configuração para as configurações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="7b072-117">[Configuration Sections Schema](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="7b072-118">[Esquema de configurações de depuração e rastreamento](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Descreve os elementos que especificam opções de rastreamento e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="7b072-118">[Trace and Debug Settings Schema](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="7b072-119">[Esquema de configurações do compilador e do provedor de linguagem](~/docs/framework/configure-apps/file-schema/compiler/index.md) Descreve os elementos que especificam a configuração do compilador para os provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="7b072-119">[Compiler and Language Provider Settings Schema](~/docs/framework/configure-apps/file-schema/compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="7b072-120">[Esquema de configurações do aplicativo](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Descreve os elementos que permitem que um aplicativo do Windows Forms ou do ASP.NET armazene e recupere configurações no escopo do aplicativo e no escopo do usuário.</span><span class="sxs-lookup"><span data-stu-id="7b072-120">[Application Settings Schema](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="7b072-121">[Esquema de configurações do aplicativo](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b072-121">[App Settings Schema](~/docs/framework/configure-apps/file-schema/appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="7b072-122">[Esquema de configurações da Web](~/docs/framework/configure-apps/file-schema/web/index.md) Todos os elementos do esquema de configurações da Web, incluindo elementos para configurar como o ASP.NET funciona com um aplicativo host, como o IIS.</span><span class="sxs-lookup"><span data-stu-id="7b072-122">[Web Settings Schema](~/docs/framework/configure-apps/file-schema/web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="7b072-123">Usado em arquivos *Aspnet.config*.</span><span class="sxs-lookup"><span data-stu-id="7b072-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="7b072-124">[Esquema de configuração do Windows Forms](winforms/index.md) Todos os elementos na seção de configuração do aplicativo do Windows Forms, incluindo personalizações, como suporte para vários monitores e para alto DPI.</span><span class="sxs-lookup"><span data-stu-id="7b072-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="7b072-125">[Esquema de configuração do WCF](~/docs/framework/configure-apps/file-schema/wcf/index.md) Todos os elementos que permitem configurar aplicativos clientes e de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="7b072-125">[WCF Configuration Schema](~/docs/framework/configure-apps/file-schema/wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="7b072-126">[Sintaxe de diretiva do WCF](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Descreve a diretiva `@ServiceHost`, que define atributos específicos da página usados pelo compilador .svc.</span><span class="sxs-lookup"><span data-stu-id="7b072-126">[WCF Directive Syntax](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="7b072-127">[Esquema de configuração do WIF](windows-identity-foundation/index.md) Todos os elementos do esquema de configuração do WIF (Windows Identity Foundation).</span><span class="sxs-lookup"><span data-stu-id="7b072-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7b072-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7b072-128">Related sections</span></span>

<span data-ttu-id="7b072-129">[Esquema de configurações remotas](https://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Descreve os elementos que configuram aplicativos clientes e para servidores que implementam a comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="7b072-129">[Remoting Settings Schema](https://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="7b072-130">[Esquema de configurações do ASP.NET](https://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Descreve os elementos que controlam o comportamento de aplicativos Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7b072-130">[ASP.NET Settings Schema](https://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="7b072-131">[Esquema de configurações de serviços Web](https://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Descreve os elementos que controlam o comportamento dos serviços Web do ASP.NET e de seus clientes.</span><span class="sxs-lookup"><span data-stu-id="7b072-131">[Web Services Settings Schema](https://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="7b072-132">[Configurando aplicativos do .NET Framework](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Descreve como configurar a segurança, associação de assembly e a comunicação remota no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b072-132">[Configuring .NET Framework Apps](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
