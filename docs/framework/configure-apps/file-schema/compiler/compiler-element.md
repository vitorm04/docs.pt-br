---
title: Elemento <compiler>
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 34753d538ff37ac4ae621f653d47ac92ac6749a0
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674458"
---
# <a name="compiler-element"></a><span data-ttu-id="6a694-102">\<compilador > elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-102">\<compiler> Element</span></span>

<span data-ttu-id="6a694-103">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="6a694-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="6a694-104">\<Elemento de configuração > \<elemento System. CodeDom > \<compiladores de elemento > \<compilador > elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="6a694-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a694-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a694-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6a694-106">Attributes and Elements</span></span>

<span data-ttu-id="6a694-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6a694-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a694-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="6a694-108">Attributes</span></span>

|<span data-ttu-id="6a694-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="6a694-109">Attribute</span></span>|<span data-ttu-id="6a694-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a694-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="6a694-111">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6a694-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6a694-112">Especifica os argumentos adicionais específicos do compilador para compilação.</span><span class="sxs-lookup"><span data-stu-id="6a694-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="6a694-113">Os valores para o `compilerOptions` atributo normalmente são listados em um tópico de opções do compilador para o compilador.</span><span class="sxs-lookup"><span data-stu-id="6a694-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="6a694-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6a694-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6a694-115">Fornece uma lista separada por ponto e vírgula de extensões de nome de arquivo usado por arquivos de origem para o provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="6a694-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="6a694-116">Por exemplo, ".cs".</span><span class="sxs-lookup"><span data-stu-id="6a694-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="6a694-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6a694-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="6a694-118">Fornece uma lista separada por vírgulas de nomes de idiomas com suporte pelo provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="6a694-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="6a694-119">Por exemplo, "C#;cs;csharp".</span><span class="sxs-lookup"><span data-stu-id="6a694-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="6a694-120">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6a694-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="6a694-121">Especifica o nome do tipo do provedor de linguagem, incluindo o nome do assembly que contém a implementação do provedor.</span><span class="sxs-lookup"><span data-stu-id="6a694-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="6a694-122">O nome do tipo deve atender aos requisitos definidos na [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6a694-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="6a694-123">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="6a694-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6a694-124">Especifica o nível de aviso do compilador padrão; Determina o nível no qual o provedor de linguagem de programação trata avisos de compilação como erros.</span><span class="sxs-lookup"><span data-stu-id="6a694-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6a694-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6a694-125">Child Elements</span></span>

|<span data-ttu-id="6a694-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-126">Element</span></span>|<span data-ttu-id="6a694-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a694-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a694-128">\<providerOption > elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-128">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="6a694-129">Especifica atributos de versão do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="6a694-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a694-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6a694-130">Parent Elements</span></span>

|<span data-ttu-id="6a694-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-131">Element</span></span>|<span data-ttu-id="6a694-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a694-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a694-133">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="6a694-133">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="6a694-134">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a694-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="6a694-135">\<System. CodeDom > elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-135">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="6a694-136">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6a694-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="6a694-137">\<compiladores > elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-137">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="6a694-138">Contêiner para elementos de configuração do compilador; contém zero ou mais `<compiler>` elementos.</span><span class="sxs-lookup"><span data-stu-id="6a694-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a694-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a694-139">Remarks</span></span>

<span data-ttu-id="6a694-140">Cada `<compiler>` elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="6a694-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="6a694-141">Estende o provedor do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> classe para um idioma específico; o `<compiler>` elemento define o compilador e as configurações do gerador de código para o provedor de linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="6a694-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="6a694-142">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6a694-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="6a694-143">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="6a694-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6a694-144">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="6a694-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="6a694-145">Elementos de compilador no arquivo de configuração Web ou aplicativo podem suplementar ou substituir as configurações no arquivo de configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="6a694-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="6a694-146">Se mais de uma implementação de provedor estiver configurada para o mesmo nome do idioma ou a mesma extensão de arquivo, a última configuração correspondente substitui quaisquer provedores anteriores configurados para essa extensão de arquivo ou nome de idioma.</span><span class="sxs-lookup"><span data-stu-id="6a694-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="6a694-147">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="6a694-147">Configuration File</span></span>

<span data-ttu-id="6a694-148">Esse elemento pode ser usado no arquivo de configuração do computador e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6a694-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="6a694-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6a694-149">Example</span></span>

<span data-ttu-id="6a694-150">O exemplo a seguir ilustra um elemento de configuração do compilador típico:</span><span class="sxs-lookup"><span data-stu-id="6a694-150">The following example illustrates a typical compiler configuration element:</span></span>

```xml
<configuration>
  <system.codedom>
    <compilers>
      <!-- zero or more compiler elements -->
      <compiler
        language="c#;cs;csharp"
        extension=".cs"
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"
        compilerOptions="/optimize"
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6a694-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a694-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="6a694-152">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6a694-152">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="6a694-153">\<compiladores > elemento</span><span class="sxs-lookup"><span data-stu-id="6a694-153">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [<span data-ttu-id="6a694-154">Especificando nomes de tipo totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="6a694-154">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="6a694-155">[Elemento de compilador para compiladores para compilação (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6a694-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
