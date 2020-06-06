---
title: Elemento <NetFx40_LegacySecurityPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116246"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="88289-102">Elemento \<NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="88289-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="88289-103">Especifica se o runtime usa a política de CAS (Segurança de Acesso do Código) herdada.</span><span class="sxs-lookup"><span data-stu-id="88289-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a><span data-ttu-id="88289-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88289-104">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88289-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="88289-105">Attributes and Elements</span></span>

<span data-ttu-id="88289-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="88289-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="88289-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="88289-107">Attributes</span></span>

|<span data-ttu-id="88289-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="88289-108">Attribute</span></span>|<span data-ttu-id="88289-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="88289-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="88289-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="88289-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="88289-111">Especifica se o tempo de execução usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="88289-111">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="88289-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="88289-112">enabled Attribute</span></span>

|<span data-ttu-id="88289-113">Valor</span><span class="sxs-lookup"><span data-stu-id="88289-113">Value</span></span>|<span data-ttu-id="88289-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="88289-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="88289-115">O tempo de execução não usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="88289-115">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="88289-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="88289-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="88289-117">O tempo de execução usa a política CAS herdada.</span><span class="sxs-lookup"><span data-stu-id="88289-117">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="88289-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="88289-118">Child Elements</span></span>

<span data-ttu-id="88289-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="88289-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88289-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="88289-120">Parent Elements</span></span>

|<span data-ttu-id="88289-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="88289-121">Element</span></span>|<span data-ttu-id="88289-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="88289-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="88289-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88289-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="88289-124">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="88289-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="88289-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="88289-125">Remarks</span></span>

<span data-ttu-id="88289-126">No .NET Framework versão 3,5 e versões anteriores, a política de CAS está sempre em vigor.</span><span class="sxs-lookup"><span data-stu-id="88289-126">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="88289-127">No .NET Framework 4, a política de CAS deve ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="88289-127">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="88289-128">A política de CAS é específica da versão.</span><span class="sxs-lookup"><span data-stu-id="88289-128">CAS policy is version-specific.</span></span> <span data-ttu-id="88289-129">As políticas de CAS personalizadas que existem em versões anteriores do .NET Framework devem ser reespecificadas no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="88289-129">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="88289-130">Aplicar o `<NetFx40_LegacySecurityPolicy>` elemento a um assembly .NET Framework 4 não afeta o [código de segurança transparente](../../../misc/security-transparent-code.md); as regras de transparência ainda se aplicam.</span><span class="sxs-lookup"><span data-stu-id="88289-130">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88289-131">A aplicação do `<NetFx40_LegacySecurityPolicy>` elemento pode resultar em penalidades de desempenho significativas para assemblies de imagem nativa criados pelo [gerador de imagem nativa (NGen. exe)](../../../tools/ngen-exe-native-image-generator.md) que não estão instalados no [cache de assembly global](../../../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="88289-131">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="88289-132">A degradação do desempenho é causada pela incapacidade do tempo de execução de carregar os assemblies como imagens nativas quando o atributo é aplicado, resultando no carregamento de assemblies just-in-time.</span><span class="sxs-lookup"><span data-stu-id="88289-132">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="88289-133">Se você especificar uma versão de .NET Framework de destino que seja anterior à .NET Framework 4 nas configurações do projeto para seu projeto do Visual Studio, a política de CAS será habilitada, incluindo as políticas CAS personalizadas especificadas para essa versão.</span><span class="sxs-lookup"><span data-stu-id="88289-133">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="88289-134">No entanto, você não poderá usar novos .NET Framework 4 tipos e membros.</span><span class="sxs-lookup"><span data-stu-id="88289-134">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="88289-135">Você também pode especificar uma versão anterior do .NET Framework usando o [ \<supportedRuntime> elemento](../startup/supportedruntime-element.md) no esquema de configurações de inicialização no arquivo de [configuração do aplicativo](../../index.md).</span><span class="sxs-lookup"><span data-stu-id="88289-135">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="88289-136">A sintaxe do arquivo de configuração diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="88289-136">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="88289-137">Você deve usar a sintaxe conforme fornecido nas seções sintaxe e exemplo.</span><span class="sxs-lookup"><span data-stu-id="88289-137">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="88289-138">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="88289-138">Configuration File</span></span>

<span data-ttu-id="88289-139">Esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88289-139">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="88289-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88289-140">Example</span></span>

<span data-ttu-id="88289-141">O exemplo a seguir mostra como habilitar a política CAS herdada para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="88289-141">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="88289-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="88289-142">See also</span></span>

- [<span data-ttu-id="88289-143">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="88289-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="88289-144">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="88289-144">Configuration File Schema</span></span>](../index.md)
