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
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039154"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="8bc2e-102">Esquema de arquivos de configuração para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8bc2e-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="8bc2e-103">Arquivos de configuração são arquivos XML padrão que você pode usar para alterar as configurações e definir diretivas para seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="8bc2e-104">O esquema de configuração do .NET Framework consiste em elementos que você pode usar em arquivos de configuração para controlar o comportamento de seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="8bc2e-105">O sumário desta seção reflete a hierarquia de esquema para inicialização, runtime, rede e outros tipos de configuração.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="8bc2e-106">Para obter informações sobre os tipos, o formato e o local dos arquivos de configuração, consulte [configurar aplicativos](../index.md).</span><span class="sxs-lookup"><span data-stu-id="8bc2e-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="8bc2e-107">Familiarize-se com XML para editar os arquivos de configuração diretamente.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bc2e-108">Os atributos e as marcas XML em arquivos de configuração diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8bc2e-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8bc2e-109">In this section</span></span>

<span data-ttu-id="8bc2e-110">[ **\<** elemento de > de configuração](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="8bc2e-111">O elemento de nível superior para todos os arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="8bc2e-112">[ **\<o elemento > assembly** ](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="8bc2e-113">Especifica a diretiva de ligação de assembly no nível de configuração.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="8bc2e-114">[ **\<elemento de > linkedConfiguration** ](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="8bc2e-115">Especifica um arquivo de configuração a ser incluído.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="8bc2e-116">\ de [esquema das configurações de inicialização](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-116">[Startup Settings Schema](./startup/index.md)\</span></span>
<span data-ttu-id="8bc2e-117">Elementos que especificam qual versão do Common Language Runtime usar.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="8bc2e-118">\ de [esquema de configurações de tempo de execução](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-118">[Runtime Settings Schema](./runtime/index.md)\</span></span>
<span data-ttu-id="8bc2e-119">Elementos que configuram Associação de assembly e comportamento de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="8bc2e-120">[Esquema de configurações de rede](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="8bc2e-121">Elementos que especificam como o .NET Framework se conecta à Internet.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="8bc2e-122">\ de [esquema de configurações de criptografia](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-122">[Cryptography Settings Schema](./cryptography/index.md)\</span></span>
<span data-ttu-id="8bc2e-123">Elementos que mapeiam nomes de algoritmos amigáveis para classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="8bc2e-124">\ de [esquema das seções de configuração](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-124">[Configuration Sections Schema](configuration-sections-schema.md)\</span></span>
<span data-ttu-id="8bc2e-125">Elementos usados para criar e usar seções de configuração para configurações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="8bc2e-126">\ [de esquema de configurações de rastreamento e depuração](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-126">[Trace and Debug Settings Schema](./trace-debug/index.md)\</span></span>
<span data-ttu-id="8bc2e-127">Elementos que especificam opções de rastreamento e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="8bc2e-128">\ [de esquema de configurações do provedor de idiomas e do compilador](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)\</span></span>
<span data-ttu-id="8bc2e-129">Elementos que especificam a configuração do compilador para provedores de idiomas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="8bc2e-130">\ de [esquema de configurações do aplicativo](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-130">[Application Settings Schema](application-settings-schema.md)\</span></span>
<span data-ttu-id="8bc2e-131">Elementos que permitem a um aplicativo Windows Forms ou ASP.NET armazenar e recuperar configurações no escopo do aplicativo e no escopo do usuário.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="8bc2e-132">\ de [esquema de configurações do aplicativo](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-132">[App Settings Schema](./appsettings/index.md)\</span></span>
<span data-ttu-id="8bc2e-133">Contém configurações de aplicativo personalizadas, como caminhos de arquivo, URLs de serviço da Web em XML ou qualquer outra informação de configuração personalizada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="8bc2e-134">\ de [esquema de configurações da Web](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-134">[Web Settings Schema](./web/index.md)\</span></span>
<span data-ttu-id="8bc2e-135">Elementos para configurar como o ASP.NET funciona com um aplicativo host como o IIS.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="8bc2e-136">Usado em arquivos *Aspnet.config*.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="8bc2e-137">\ [esquema de configuração do Windows Forms](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-137">[Windows Forms Configuration Schema](winforms/index.md)\</span></span>
<span data-ttu-id="8bc2e-138">Todos os elementos na seção de configuração Windows Forms aplicativo, que inclui personalizações, como suporte a vários monitores e alto DPI.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="8bc2e-139">\ de [esquema de configuração do WCF](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-139">[WCF Configuration Schema](./wcf/index.md)\</span></span>
<span data-ttu-id="8bc2e-140">Todos os elementos que permitem que você configure aplicativos cliente e serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="8bc2e-141">\ de [sintaxe de diretiva WCF](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-141">[WCF Directive Syntax](./wcf-directive/index.md)\</span></span>
<span data-ttu-id="8bc2e-142">Descreve a diretiva `@ServiceHost`, que define os atributos específicos da página usados pelo compilador. svc.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="8bc2e-143">[Esquema de configuração do WIF](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="8bc2e-143">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="8bc2e-144">Todos os elementos do esquema de configuração do Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="8bc2e-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="8bc2e-145">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8bc2e-145">Related sections</span></span>

<span data-ttu-id="8bc2e-146">\ de [esquema de configurações de comunicação remota](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8bc2e-146">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\</span></span>
<span data-ttu-id="8bc2e-147">Descreve os elementos que configuram aplicativos cliente e servidor que implementam a comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="8bc2e-148">\ de [esquema de configurações de ASP.net](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8bc2e-148">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\</span></span>
<span data-ttu-id="8bc2e-149">Descreve os elementos que controlam o comportamento de aplicativos da Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="8bc2e-150">\ de [esquema de configurações de serviços Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8bc2e-150">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\</span></span>
<span data-ttu-id="8bc2e-151">Descreve os elementos que controlam o comportamento de serviços da Web ASP.NET e de seus clientes.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="8bc2e-152">[Configurando aplicativos .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8bc2e-152">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="8bc2e-153">Descreve como configurar a segurança, ligação de assembly e comunicação remota do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bc2e-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
