---
title: Elemento <NetFx40_LegacySecurityPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cd6f937811ae503dd4de7ff989510c4eb8b8933
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252441"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="ef83a-102">\<Elemento de > NetFx40_LegacySecurityPolicy</span><span class="sxs-lookup"><span data-stu-id="ef83a-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="ef83a-103">Especifica se o tempo de execução usa a política de CAS (Segurança de Acesso do Código) herdada.</span><span class="sxs-lookup"><span data-stu-id="ef83a-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

<span data-ttu-id="ef83a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ef83a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ef83a-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ef83a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ef83a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> NetFx40_LegacySecurityPolicy**</span><span class="sxs-lookup"><span data-stu-id="ef83a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ef83a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef83a-107">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef83a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ef83a-108">Attributes and Elements</span></span>

<span data-ttu-id="ef83a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ef83a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef83a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ef83a-110">Attributes</span></span>

|<span data-ttu-id="ef83a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef83a-111">Attribute</span></span>|<span data-ttu-id="ef83a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef83a-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ef83a-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ef83a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ef83a-114">Especifica se o tempo de execução usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="ef83a-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ef83a-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="ef83a-115">enabled Attribute</span></span>

|<span data-ttu-id="ef83a-116">Valor</span><span class="sxs-lookup"><span data-stu-id="ef83a-116">Value</span></span>|<span data-ttu-id="ef83a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef83a-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ef83a-118">O tempo de execução não usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="ef83a-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="ef83a-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ef83a-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="ef83a-120">O tempo de execução usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="ef83a-120">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ef83a-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ef83a-121">Child Elements</span></span>

<span data-ttu-id="ef83a-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ef83a-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef83a-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ef83a-123">Parent Elements</span></span>

|<span data-ttu-id="ef83a-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef83a-124">Element</span></span>|<span data-ttu-id="ef83a-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef83a-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ef83a-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef83a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ef83a-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ef83a-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef83a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef83a-128">Remarks</span></span>

<span data-ttu-id="ef83a-129">No .NET Framework versão 3,5 e versões anteriores, a política de CAS está sempre em vigor.</span><span class="sxs-lookup"><span data-stu-id="ef83a-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="ef83a-130">No .NET Framework 4, a política de CAS deve ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="ef83a-130">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="ef83a-131">A política de CAS é específica da versão.</span><span class="sxs-lookup"><span data-stu-id="ef83a-131">CAS policy is version-specific.</span></span> <span data-ttu-id="ef83a-132">As políticas de CAS personalizadas que existem em versões anteriores do .NET Framework devem ser reespecificadas no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ef83a-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="ef83a-133">Aplicar o `<NetFx40_LegacySecurityPolicy>` elemento a um assembly .NET Framework 4 não afeta o [código de segurança transparente](../../../misc/security-transparent-code.md); as regras de transparência ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="ef83a-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef83a-134">A aplicação `<NetFx40_LegacySecurityPolicy>` do elemento pode resultar em penalidades de desempenho significativas para assemblies de imagem nativa criados pelo [gerador de imagem nativa (NGen. exe)](../../../tools/ngen-exe-native-image-generator.md) que não estão instalados no [cache de assembly global](../../../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="ef83a-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="ef83a-135">A degradação do desempenho é causada pela incapacidade do tempo de execução de carregar os assemblies como imagens nativas quando o atributo é aplicado, resultando no carregamento de assemblies just-in-time.</span><span class="sxs-lookup"><span data-stu-id="ef83a-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="ef83a-136">Se você especificar uma versão de .NET Framework de destino que seja anterior à .NET Framework 4 nas configurações do projeto para seu projeto do Visual Studio, a política de CAS será habilitada, incluindo as políticas CAS personalizadas especificadas para essa versão.</span><span class="sxs-lookup"><span data-stu-id="ef83a-136">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="ef83a-137">No entanto, você não poderá usar novos .NET Framework 4 tipos e membros.</span><span class="sxs-lookup"><span data-stu-id="ef83a-137">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="ef83a-138">Você também pode especificar uma versão anterior do .NET Framework usando o [ \<elemento supportedRuntime >](../startup/supportedruntime-element.md) no esquema de configurações de inicialização no arquivo de [configuração do aplicativo](../../index.md).</span><span class="sxs-lookup"><span data-stu-id="ef83a-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ef83a-139">A sintaxe do arquivo de configuração diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ef83a-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="ef83a-140">Você deve usar a sintaxe conforme fornecido nas seções sintaxe e exemplo.</span><span class="sxs-lookup"><span data-stu-id="ef83a-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="ef83a-141">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="ef83a-141">Configuration File</span></span>

<span data-ttu-id="ef83a-142">Esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef83a-142">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="ef83a-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef83a-143">Example</span></span>

<span data-ttu-id="ef83a-144">O exemplo a seguir mostra como habilitar a política CAS herdada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef83a-144">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ef83a-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef83a-145">See also</span></span>

- [<span data-ttu-id="ef83a-146">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ef83a-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ef83a-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="ef83a-147">Configuration File Schema</span></span>](../index.md)
